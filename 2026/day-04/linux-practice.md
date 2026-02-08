**1) Process Checks**
Command 1: Check running processes

ubuntu@ip-192-168-0-14:~$ ps aux | head
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  1.1  1.4  22528 13836 ?        Ss   07:22   0:01 /sbin/init
root           2  0.0  0.0      0     0 ?        S    07:22   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    07:22   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   07:22   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0      0     0 ?        I<   07:22   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0      0     0 ?        I<   07:22   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7  0.0  0.0      0     0 ?        I<   07:22   0:00 [kworker/R-slub_flushwq]
root           8  0.0  0.0      0     0 ?        I<   07:22   0:00 [kworker/R-netns]
root           9  0.0  0.0      0     0 ?        I    07:22   0:00 [kworker/0:0-cgroup_destroy]

==================================================================================================================================================================

Verify nginx processes

ubuntu@ip-192-168-0-14:~$ ps aux | grep nginx
root        1207  0.0  0.7  11196  7088 ?        S    07:23   0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
www-data    1209  0.0  0.4  12884  4568 ?        S    07:23   0:00 nginx: worker process
www-data    1210  0.0  0.4  12884  4520 ?        S    07:23   0:00 nginx: worker process
ubuntu      1297  0.0  0.2   7076  2228 pts/0    S+   07:30   0:00 grep --color=auto nginx

=================================================================================================================================================================
**Command 2: Live CPU & memory view**
top
top - 07:27:08 up 4 min,  1 user,  load average: 0.00, 0.02, 0.00
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :    914.2 total,    333.8 free,    377.2 used,    365.7 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.    537.0 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1283 ubuntu    20   0   12368   5888   3660 R   0.3   0.6   0:00.01 top
      1 root      20   0   22528  13836   9600 S   0.0   1.5   0:01.54 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns
      9 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0-cgroup_destroy
     10 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri
     11 root      20   0       0      0      0 I   0.0   0.0   0:00.01 kworker/0:1-events
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.07 kworker/u8:0-kvfree_rcu_reclaim
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq
     14 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread
     15 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.01 ksoftirqd/0
     17 root      20   0       0      0      0 I   0.0   0.0   0:00.06 rcu_sched
     18 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0
     19 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_gp_kthread_worker
     20 root      rt   0       0      0      0 S   0.0   0.0   0:00.00 migration/0
     21 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0
     22 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0
     23 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1
     24 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1
     25 root      rt   0       0      0      0 S   0.0   0.0   0:00.06 migration/1
     26 root      20   0       0      0      0 S   0.0   0.0   0:00.01 ksoftirqd/1
     27 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0-cgroup_destroy
     28 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri
     29 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kdevtmpfs
     30 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-inet_frag_wq
     31 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kauditd
     32 root      20   0       0      0      0 S   0.0   0.0   0:00.00 khungtaskd
     33 root      20   0       0      0      0 I   0.0   0.0   0:00.04 kworker/u8:1-events_unbound
     
=========================================================================================================================================================

2) Service Checks (systemd)

ubuntu@ip-192-168-0-14:~$ systemctl status nginx
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
     Active: active (running) since Sun 2026-02-08 07:23:44 UTC; 6min ago
       Docs: man:nginx(8)
    Process: 1175 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
    Process: 1177 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
   Main PID: 1207 (nginx)
      Tasks: 3 (limit: 1017)
     Memory: 2.4M (peak: 5.3M)
        CPU: 24ms
     CGroup: /system.slice/nginx.service
             ├─1207 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
             ├─1209 "nginx: worker process"
             └─1210 "nginx: worker process"
             
  ==========================================================================================================================================================

**Command 4: Confirm nginx is running under systemd**

  ubuntu@ip-192-168-0-14:~$ systemctl list-units --type=service | grep nginx
  nginx.service                                  loaded active running A high performance web server and a reverse proxy serve
  
============================================================================================================================================================

3) Log Checks
   
**Command 5: Inspect nginx logs via journald**
     ubuntu@ip-192-168-0-14:~$ journalctl -u nginx
Feb 08 07:23:44 ip-192-168-0-14 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Feb 08 07:23:44 ip-192-168-0-14 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.

===========================================================================================================================================================
Command 6: Check access/error logs directly

ubuntu@ip-192-168-0-14:/var/log$ tail -n 20 syslog
2026-02-08T07:27:51.199109+00:00 ip-192-168-0-14 systemd[1]: update-notifier-download.service: Deactivated successfully.
2026-02-08T07:27:51.199261+00:00 ip-192-168-0-14 systemd[1]: Finished update-notifier-download.service - Download data for packages that failed at package install time.
2026-02-08T07:27:53.084240+00:00 ip-192-168-0-14 dbus-daemon[517]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.12' (uid=0 pid=539 comm="/usr/lib/snapd/snapd" label="unconfined")
2026-02-08T07:27:53.092237+00:00 ip-192-168-0-14 systemd[1]: Starting systemd-timedated.service - Time & Date Service...
2026-02-08T07:27:53.131838+00:00 ip-192-168-0-14 dbus-daemon[517]: [system] Successfully activated service 'org.freedesktop.timedate1'
2026-02-08T07:27:53.131944+00:00 ip-192-168-0-14 systemd[1]: Started systemd-timedated.service - Time & Date Service.
2026-02-08T07:28:23.164531+00:00 ip-192-168-0-14 systemd[1]: systemd-timedated.service: Deactivated successfully.
2026-02-08T07:28:55.131095+00:00 ip-192-168-0-14 PackageKit: daemon quit
2026-02-08T07:28:55.137464+00:00 ip-192-168-0-14 systemd[1]: packagekit.service: Deactivated successfully.
2026-02-08T07:29:07.162184+00:00 ip-192-168-0-14 systemd[843]: launchpadlib-cache-clean.service - Clean up old files in the Launchpadlib cache was skipped because of an unmet condition check (ConditionPathExists=/home/ubuntu/.launchpadlib/api.launchpad.net/cache).
2026-02-08T07:30:07.169787+00:00 ip-192-168-0-14 systemd[1]: Starting sysstat-collect.service - system activity accounting tool...
2026-02-08T07:30:07.173792+00:00 ip-192-168-0-14 systemd[1]: sysstat-collect.service: Deactivated successfully.
2026-02-08T07:30:07.174002+00:00 ip-192-168-0-14 systemd[1]: Finished sysstat-collect.service - system activity accounting tool.
2026-02-08T07:35:01.877546+00:00 ip-192-168-0-14 CRON[1329]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
2026-02-08T07:37:51.083315+00:00 ip-192-168-0-14 systemd[1]: Starting systemd-tmpfiles-clean.service - Cleanup of Temporary Directories...
2026-02-08T07:37:51.100390+00:00 ip-192-168-0-14 systemd[1]: systemd-tmpfiles-clean.service: Deactivated successfully.
2026-02-08T07:37:51.100624+00:00 ip-192-168-0-14 systemd[1]: Finished systemd-tmpfiles-clean.service - Cleanup of Temporary Directories.
2026-02-08T07:40:07.168119+00:00 ip-192-168-0-14 systemd[1]: Starting sysstat-collect.service - system activity accounting tool...
2026-02-08T07:40:07.173759+00:00 ip-192-168-0-14 systemd[1]: sysstat-collect.service: Deactivated successfully.
2026-02-08T07:40:07.173969+00:00 ip-192-168-0-14 systemd[1]: Finished sysstat-collect.service - system activity accounting tool.

===========================================================================================================================================================

4) Mini Troubleshooting Flow (Real Incident Style)
Scenario: “Website not loading”

Step-by-step checks:

Is nginx running?
systemctl status nginx

Are processes alive?
ps aux | grep nginx

Is nginx listening on port 80/443?
ss -lntup | grep nginx

Any recent errors?
ubuntu@ip-192-168-0-14:/$ journalctl -u nginx
tail -n 50 /var/log/nginx/error.log

Feb 08 07:23:44 ip-192-168-0-14 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Feb 08 07:23:44 ip-192-168-0-14 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
2026/02/08 07:23:44 [notice] 1207#1207: using inherited sockets from "5;6;"

