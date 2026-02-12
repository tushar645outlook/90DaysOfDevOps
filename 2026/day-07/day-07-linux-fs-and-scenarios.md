**purpose of these essential directories In Linux**

(root) : /) - The starting point of everything. it is the highest-level directory in the Linux file system hierarchy. 
Its primary purpose is to serve as the starting point and organizational foundation for all other files, directories, and mounted file systems on the system

ubuntu@ip-192-168-0-93:/$ ls
bin                boot  etc   lib                lib64       media  opt   root  sbin                snap  sys  usr
bin.usr-is-merged  dev   home  lib.usr-is-merged  lost+found  mnt    proc  run   sbin.usr-is-merged  srv   tmp  var

I would use this when…
I need to understand the overall system structure or navigate to major system directories.

===================================================================================================================================================================

/home: User home directories. Home directories for regular users.

ubuntu@ip-192-168-0-93:/home$ ls
ubuntu

I would use this when…
I need to check user files, scripts, SSH keys, or disk usage for a specific user.

======================================================================================================================================================================

/root: Root user's home directory. Home directory of the root (administrator) user.

root@ip-192-168-0-93:~# ls
snap

I would use this when…
Working as root and checking admin-level scripts or configurations.

============================================================================================================================================================================

/etc: Configuration files. System-wide configuration files.

root@ip-192-168-0-93:~# ls /etc/
ModemManager            dpkg                 libblockdev             pam.conf       sos
PackageKit              e2scrub.conf         libibverbs.d            pam.d          ssh
X11                     ec2_version          libnl-3                 passwd         ssl
acpi                    environment          locale.alias            passwd-        subgid
adduser.conf            ethertypes           locale.conf             perl           subgid-
alternatives            fstab                locale.gen              pki            subuid
apparmor                fuse.conf            localtime               plymouth       subuid-
apparmor.d              fwupd                logcheck                pm             sudo.conf
apport                  gai.conf             login.defs              polkit-1       sudo_logsrvd.conf
apt                     gnutls               logrotate.conf          pollinate      sudoers
bash.bashrc             groff                logrotate.d             ppp            sudoers.d
bash_completion         group                lsb-release             profile        supercat
bash_completion.d       group-               lvm                     profile.d      sysctl.conf
bindresvport.blacklist  grub.d               machine-id              protocols      sysctl.d
binfmt.d                gshadow              magic                   python3        sysstat
byobu                   gshadow-             magic.mime              python3.12     systemd
ca-certificates         gss                  manpath.config          rc0.d          terminfo
ca-certificates.conf    hdparm.conf          mdadm                   rc1.d          timezone
chrony                  hibagent-config.cfg  mime.types              rc2.d          tmpfiles.d
cloud                   hibinit-config.cfg   mke2fs.conf             rc3.d          ubuntu-advantage
console-setup           host.conf            modprobe.d              rc4.d          ucf.conf
credstore               hostname             modules                 rc5.d          udev
credstore.encrypted     hosts                modules-load.d          rc6.d          udisks2
cron.d                  hosts.allow          mtab                    rcS.d          ufw
cron.daily              hosts.deny           multipath               resolv.conf    update-manager
cron.hourly             init.d               multipath.conf          rmt            update-motd.d
cron.monthly            initramfs-tools      nanorc                  rpc            update-notifier
cron.weekly             inputrc              needrestart             rsyslog.conf   usb_modeswitch.conf
cron.yearly             iproute2             netconfig               rsyslog.d      usb_modeswitch.d
crontab                 iscsi                netplan                 screenrc       vconsole.conf
cryptsetup-initramfs    issue                network                 security       vim
crypttab                issue.net            networkd-dispatcher     selinux        vmware-tools
dbus-1                  kernel               networks                sensors.d      vtrgb
debconf.conf            landscape            newt                    sensors3.conf  wgetrc
debian_version          ld.so.cache          nftables.conf           services       xattr.conf
default                 ld.so.conf           nsswitch.conf           sgml           xdg
deluser.conf            ld.so.conf.d         opt                     shadow         xml
depmod.d                ldap                 os-release              shadow-        zsh_command_not_found
dhcp                    legal                overlayroot.conf        shells
dhcpcd.conf             libaudit.conf        overlayroot.local.conf  skel

I would use this when…
Troubleshooting configuration issues (SSH, hostname, networking, services).

====================================================================================================================================================================

/var/log - Log files. System and application log files.

ubuntu@ip-192-168-0-93:~$ ls /var/log
README            apport.log  btmp                   cloud-init.log  dmesg.0     dpkg.log  landscape  syslog               wtmp
alternatives.log  apt         chrony                 dist-upgrade    dmesg.1.gz  journal   lastlog    sysstat
amazon            auth.log    cloud-init-output.log  dmesg           dmesg.2.gz  kern.log  private    unattended-upgrades

I would use this when…
Investigating service failures, login issues, or production incidents

===================================================================================================================================================================

/tmp - Temporary files. Temporary files created by users and applications.

ubuntu@ip-192-168-0-93:~$ ls /tmp/
snap-private-tmp
systemd-private-280be23e354047bf9b520143be03eae8-ModemManager.service-Zmfpll
systemd-private-280be23e354047bf9b520143be03eae8-chrony.service-PlsCf3
systemd-private-280be23e354047bf9b520143be03eae8-polkit.service-PeEM5j
systemd-private-280be23e354047bf9b520143be03eae8-systemd-logind.service-hMn6QF
systemd-private-280be23e354047bf9b520143be03eae8-systemd-resolved.service-ePamGy

I would use this when…
Checking for temporary file buildup or troubleshooting app runtime issues.

=================================================================================================================================================================

**Additional Directories (Good to Know):**

/bin - Essential command binaries. Essential system binaries (basic commands).

ubuntu@ip-192-168-0-93:~$ ls /bin
 NF                                   git-shell                          on_ac_power                 sgp_dd
 VGAuthService                        git-upload-archive                 openssl                     sh
'['                                   git-upload-pack                    openvt                      sha1sum
 aa-enabled                           glib-compile-schemas               os-prober                   sha224sum
 aa-exec                              gpasswd                            pager                       sha256sum

 I would use this when…
Verifying core commands exist in minimal system environments.

====================================================================================================================================================================

/usr/bin - User command binaries. User-level command binaries and installed applications.

ubuntu@ip-192-168-0-93:~$ ls /usr/bin/
 NF                                   git-shell                          on_ac_power                 sgp_dd
 VGAuthService                        git-upload-archive                 openssl                     sh
'['                                   git-upload-pack                    openvt                      sha1sum

I would use this when…
Checking installed applications and troubleshooting missing commands.

===================================================================================================================================================================

/opt - Optional/third-party applications. Optional or third-party software installations.

ubuntu@ip-192-168-0-93:~$ ls /opt/

I would use this when…
Managing enterprise applications installed outside default package locations.

======================================================================================================================================================================

**Hands-on task:**

Find the largest log file in /var/log

ubuntu@ip-192-168-0-93:~$ du -sh /var/log/* 2>/dev/null | sort -h | tail -5
236K    /var/log/kern.log
452K    /var/log/cloud-init.log
548K    /var/log/sysstat
784K    /var/log/syslog
43M     /var/log/journal

Helps identify disk space issues due to logs.

=======================================================================================

cat /etc/hostname

ubuntu@ip-192-168-0-93:~$ cat /etc/hostname
ip-192-168-0-93

Confirms system identity (important in multi-server environments).

=======================================================================================

ls -la ~

ubuntu@ip-192-168-0-93:~$ ls -la ~
total 36
drwxr-x--- 4 ubuntu ubuntu 4096 Feb 11 10:25 .
drwxr-xr-x 3 root   root   4096 Feb  9 09:15 ..
-rw------- 1 ubuntu ubuntu 1140 Feb 12 09:47 .bash_history
-rw-r--r-- 1 ubuntu ubuntu  220 Mar 31  2024 .bash_logout
-rw-r--r-- 1 ubuntu ubuntu 3771 Mar 31  2024 .bashrc
drwx------ 2 ubuntu ubuntu 4096 Feb  9 09:15 .cache
-rw-r--r-- 1 ubuntu ubuntu  807 Mar 31  2024 .profile
drwx------ 2 ubuntu ubuntu 4096 Feb  9 09:15 .ssh
-rw-r--r-- 1 ubuntu ubuntu    0 Feb  9 09:23 .sudo_as_admin_successful
-rw-rw-r-- 1 ubuntu ubuntu  278 Feb 11 10:47 notes.txt

Shows hidden files

=====================================================================================================================================================================

**Part 2: Scenario-Based Practice**

Question: How do you check if the 'nginx' service is running?

Step 1: Check service status

systemctl status nginx
Why this command? It shows if the service is active, failed, or stopped

Step 2: If service is not found, list all services

systemctl list-units --type=service
Why this command? To see what services exist on the system

Step 3: Check if service is enabled on boot

systemctl is-enabled nginx

===========================================================================================

Scenario 2: High CPU Usage

Step 1:
top

top - 10:46:42 up  1:47,  4 users,  load average: 0.00, 0.00, 0.00
Tasks: 131 total,   1 running, 130 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :    914.2 total,    209.8 free,    363.2 used,    504.4 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.    551.0 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1444 root      20   0       0      0      0 I   0.3   0.0   0:00.30 kworker/1:3-events
      1 root      20   0   22736  13968   9592 S   0.0   1.5   0:02.20 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release

Why: Live view of CPU usage.

Step 2:
ps aux --sort=-%cpu | head -10

ubuntu@ip-192-168-0-93:~$ ps aux --sort=-%cpu | head -10
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         547  0.0  4.2 1849916 39460 ?       Ssl  08:59   0:02 /snap/snapd/current/usr/lib/snapd/snapd
ubuntu      2566  0.0  0.7  14996  7184 ?        S    10:42   0:00 sshd: ubuntu@pts/6
root           1  0.0  1.4  22736 13968 ?        Ss   08:59   0:02 /sbin/init
root         545  0.0  2.1 1830608 20044 ?       Ssl  08:59   0:01 /snap/amazon-ssm-agent/12322/amazon-ssm-agent
root        2844  0.0  2.2 373076 20836 ?        Ssl  10:42   0:00 /usr/libexec/packagekitd
root        1747  0.0  0.0      0     0 ?        I    10:10   0:00 [kworker/0:2-events]
ubuntu      2567  0.0  0.5   9056  5436 pts/6    Ss   10:42   0:00 -bash
root        1444  0.0  0.0      0     0 ?        I    10:00   0:00 [kworker/1:3-events]
root         128  0.0  1.6  66912 15692 ?        S<s  08:59   0:00 /usr/lib/systemd/systemd-journald

Why: Show top CPU-consuming processes.

Step 3:
ps -fp <PID>

ubuntu@ip-192-168-0-93:~$ ps -fp 2566
UID          PID    PPID  C STIME TTY          TIME CMD
ubuntu      2566    2510  0 10:42 ?        00:00:00 sshd: ubuntu@pts/6

Why: Inspect details of suspicious process.

=======================================================================================================================================

Scenario 4: File Permissions Issue

A script at /home/user/backup.sh is not executing.
When you run it: ./backup.sh
You get: "Permission denied"

What commands would you use to fix this?

Step 1: Check current permissions
Command: ls -l /home/user/backup.sh

ubuntu@ip-192-168-0-93:~$ ls -l backup.sh
-rw-rw-r-- 1 ubuntu ubuntu 252 Feb 12 11:12 backup.sh

Look for: -rw-r--r-- (notice no 'x' = not executable)

Step 2: Add execute permission

ubuntu@ip-192-168-0-93:~$ chmod +x backup.sh

Command: chmod +x /home/user/backup.sh

Step 3: Verify it worked
Command: ls -l /home/user/backup.sh

ubuntu@ip-192-168-0-93:~$ ls -l backup.sh
-rwxrwxr-x 1 ubuntu ubuntu 252 Feb 12 11:12 backup.sh

Look for: -rwxr-xr-x (notice 'x' = executable)

Step 4: Try running it
Command: ./backup.sh

ubuntu@ip-192-168-0-93:~$ ./backup.sh
tar: Removing leading `/' from member namestar (child): /backup/backup_2026-02-12_11-16-14.tar.gz: Cannot open
: No such file or directory
tar (child): Error is not recoverable: exiting now
/var/www/
/var/www/html/
/var/www/html/index.nginx-debian.html
tar: /backup/backup_2026-02-12_11-16-14.tar.gz: Cannot write: Broken pipe
tar: Child returned status 2
tar: Error is not recoverable: exiting now
Backup completed successfully!
