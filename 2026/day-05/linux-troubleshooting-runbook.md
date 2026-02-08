Environment basics
Command 1

"ubuntu@ip-192-168-0-14:~$ uname -a
Linux ip-192-168-0-14 6.14.0-1018-aws #18~24.04.1-Ubuntu SMP Mon Nov 24 19:46:27 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux"

Observed:
Linux kernel 5.x, x86_64 — standard Ubuntu kernel, nothing unusual.

=================================================================================================================================================================
Command 2
cat /etc/os-release

ubuntu@ip-192-168-0-14:~$ cat /etc/os-release
PRETTY_NAME="Ubuntu 24.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.3 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

Observed:
Ubuntu 24.04 LTS — known-good, long-term support OS.

=================================================================================================================================================================

Filesystem sanity check

mkdir /tmp/runbook-demo
cp /etc/hosts /tmp/runbook-demo/hosts-copy
ls -l /tmp/runbook-demo

ubuntu@ip-192-168-0-14:~$ mkdir /tmp/runbook-demo
ubuntu@ip-192-168-0-14:~$ cd /tmp/
ubuntu@ip-192-168-0-14:/tmp$ ls
runbook-demo
snap-private-tmp
systemd-private-c809654a28da4e069ffe5cd9a8ca7542-ModemManager.service-sJPssP
systemd-private-c809654a28da4e069ffe5cd9a8ca7542-chrony.service-WfLcho
systemd-private-c809654a28da4e069ffe5cd9a8ca7542-polkit.service-tDt83z
systemd-private-c809654a28da4e069ffe5cd9a8ca7542-systemd-logind.service-iM7y2S
systemd-private-c809654a28da4e069ffe5cd9a8ca7542-systemd-resolved.service-gkrHYk
ubuntu@ip-192-168-0-14:/$ cp /etc/hosts /tmp/runbook-demo/host-copy
ubuntu@ip-192-168-0-14:/$ ls -l /tmp/runbook-demo/
total 4
-rw-r--r-- 1 ubuntu ubuntu 221 Feb  8 15:33 host-copy
ubuntu@ip-192-168-0-14:/$ cat /tmp/runbook-demo/host-copy
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Observed:
Filesystem is writable, permissions normal — no read-only or disk failure symptoms.

==========================================================================================================================================================

Snapshot: CPU & Memory
Command 4
ps -o pid,pcpu,pmem,comm -C nginx

ubuntu@ip-192-168-0-14:/$ ps -o pid,pcpu,pmem,comm -C nginx
    PID %CPU %MEM COMMAND
    595  0.0  0.1 nginx
    598  0.0  0.4 nginx
    599  0.0  0.5 nginx

Observed:
CPU and memory usage low — nginx not under stress

==========================================================================================================================================================

Command 5
free -h

ubuntu@ip-192-168-0-14:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           914Mi       366Mi       443Mi       2.7Mi       260Mi       547Mi
Swap:             0B          0B          0B

Observed:
Plenty of free memory, no swap pressure — memory not a bottleneck.

=========================================================================================================================================================

Snapshot: Disk & IO
df -h

ubuntu@ip-192-168-0-14:~$ df -h
Filesystem       Size  Used Avail Use% Mounted on
/dev/root         19G  1.9G   17G  11% /
tmpfs            458M     0  458M   0% /dev/shm
tmpfs            183M  876K  182M   1% /run
tmpfs            5.0M     0  5.0M   0% /run/lock
efivarfs         128K  3.8K  120K   4% /sys/firmware/efi/efivars
/dev/nvme0n1p16  881M   89M  730M  11% /boot
/dev/nvme0n1p15  105M  6.2M   99M   6% /boot/efi
tmpfs             92M   12K   92M   1% /run/user/1000

Observed:
Root filesystem <70% used — no disk-full risk.

=============================================================================================================================================================

Command 7
du -sh /var/log

ubuntu@ip-192-168-0-14:~$ sudo du -sh /var/log
51M     /var/log

Observed:
Logs consuming reasonable space — no runaway logging.

=============================================================================================================================================================

Snapshot: Network
Command 8
ss -tulpn | grep nginx

ubuntu@ip-192-168-0-14:~$ sudo ss -tulpn | grep nginx
tcp   LISTEN 0      511              0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=613,fd=5),("nginx",pid=612,fd=5),("nginx",pid=606,fd=5))
tcp   LISTEN 0      511                 [::]:80           [::]:*    users:(("nginx",pid=613,fd=6),("nginx",pid=612,fd=6),("nginx",pid=606,fd=6))

Observed:
nginx is listening on port 80 as expected.

============================================================================================================================================================

Command 9
curl -I http://localhost

ubuntu@ip-192-168-0-14:~$ curl -I http://localhost
HTTP/1.1 200 OK
Server: nginx/1.24.0 (Ubuntu)
Date: Sun, 08 Feb 2026 17:12:52 GMT
Content-Type: text/html
Content-Length: 615
Last-Modified: Sun, 08 Feb 2026 07:23:44 GMT
Connection: keep-alive
ETag: "69883a00-267"
Accept-Ranges: bytes

Observed:
Service responds successfully — network path OK locally.

============================================================================================================================================================

Logs reviewed
Command 10
journalctl -u nginx -n 50

ubuntu@ip-192-168-0-14:~$ journalctl -u nginx -n 50
Feb 08 07:23:44 ip-192-168-0-14 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Feb 08 07:23:44 ip-192-168-0-14 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
Feb 08 07:56:02 ip-192-168-0-14 systemd[1]: Stopping nginx.service - A high performance web server and a reverse proxy server...
Feb 08 07:56:02 ip-192-168-0-14 systemd[1]: nginx.service: Deactivated successfully.
Feb 08 07:56:02 ip-192-168-0-14 systemd[1]: Stopped nginx.service - A high performance web server and a reverse proxy server.
-- Boot c809654a28da4e069ffe5cd9a8ca7542 --
Feb 08 15:26:29 ip-192-168-0-14 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Feb 08 15:26:30 ip-192-168-0-14 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
Feb 08 16:21:02 ip-192-168-0-14 systemd[1]: Stopping nginx.service - A high performance web server and a reverse proxy server...
Feb 08 16:21:02 ip-192-168-0-14 systemd[1]: nginx.service: Deactivated successfully.
Feb 08 16:21:02 ip-192-168-0-14 systemd[1]: Stopped nginx.service - A high performance web server and a reverse proxy server.
-- Boot 09db638645944e878d550ec32d2d5e38 --
Feb 08 16:59:46 ip-192-168-0-14 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Feb 08 16:59:46 ip-192-168-0-14 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.

Observed:
No recent errors, clean startup messages only.

===============================================================================================================================================================

Command 11
tail -n 50 /var/log/nginx/error.log

ubuntu@ip-192-168-0-14:~$ tail -n 50 /var/log/nginx/error.log
2026/02/08 07:23:44 [notice] 1207#1207: using inherited sockets from "5;6;"

Observed:
No critical errors (no bind failures, no permission issues).

===============================================================================================================================================================

Quick findings

nginx process healthy (low CPU/memory)
Service running and listening on expected port
Disk, logs, and filesystem normal
No errors in recent logs
Issue not at OS or nginx service level

========================================================================================================================================================

If this worsens (next steps)

**Restart safely**
systemctl reload nginx
systemctl restart nginx

Watch CPU, memory, and logs during restart.

**Increase visibility**
Enable debug logging in nginx
Check upstream/backend service health

**Deep diagnostics**
strace -p <nginx_pid> for hangs
Capture traffic (tcpdump) if network-related
Check kernel logs: dmesg

============================================================================================================================================================

Why this runbook works
Same flow works for docker, ssh, cron, kubelet
Forces you to check system → service → logs → network
Reusable under pressure
Prevents random guessing during incidents
