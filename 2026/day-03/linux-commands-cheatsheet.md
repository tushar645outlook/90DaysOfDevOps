**Linux Production Troubleshooting – Command Cheat Sheet**

  Faster inspection = faster recovery
  Logs + processes + network = 90% of incidents

**1) Process Management (CPU / Memory / Hung Services)**
ps aux → (Snapshot of all processes + CPU & memory usage)

ps -ef | grep <proc> → (Check if a process is running & its parent)

top → (Live CPU, memory, load average)

htop → (Interactive process viewer (kill, sort, tree))

uptime → (System load & how long it’s been running)

free -h → (Memory usage (RAM + swap) in human format)

vmstat 1 → (CPU wait, memory pressure, I/O symptoms)

pidstat -p <pid> 1 → (Per-process CPU/memory over time)

kill -15 <pid> → (Graceful process shutdown)

kill -9 <pid> → (Force kill (last resort))

==================================================================================================================================================================

**2) systemd & Logs (Service Failures)**

systemctl status <service> → (Current state, exit code, last errors)

systemctl restart <service> → (Restart service cleanly)

systemctl is-active <service> → (Quick health check (script-friendly))

journalctl -u <service> → (Service-specific logs)

journalctl -xe → (System errors with context)

journalctl --since "10 min ago" → (Recent events during incident window)

======================================================================================================================================================================

**3) File System & Disk Issues**

df -h → (Disk space usage (first check when things break))

du -sh * | sort -h → (Find large directories fast)

ls -lh → (File sizes & permissions)

stat <file> → (Ownership, timestamps, inode info)

mount | column -t → (Mounted filesystems (NFS issues show here))

lsof +D /path → (Which process is using files in a directory)

lsof -i → (Processes holding network/file handles)

=====================================================================================================================================================================

**4) Networking Troubleshooting (Production Reality)**

ip addr → (Interface IPs (replacement for ifconfig))

ip route → (Default gateway & routing issues)

ss -lntup → (Listening ports & owning processes)

ping <host> → (Basic connectivity & packet loss)

traceroute <host> → (Where traffic is dropping)

curl -v http://host:port → (App-level connectivity & HTTP errors)

curl -I https://site → (Fast check for HTTP status & headers)

dig domain.com → (DNS resolution & TTL issues)

nc -zv host port → (Check if a port is reachable)

=================================================================================================================================================================

**5) Quick Incident Combos (Use These Together)**

High CPU?
→ top → pidstat → ps -fp <pid>

Service down?
→ systemctl status → journalctl -u

Disk full?
→ df -h → du -sh → lsof

App not reachable?
→ ss -lntup → curl → ip route

===================================================================================================================================================================

**Why This Cheat Sheet Works**

The faster you inspect processes, logs, and network, the faster you:

Restore service

Reduce downtime

Gain trust as a reliable operator

👉 These commands never get old
👉 This is muscle memory for DevOps & SREs
