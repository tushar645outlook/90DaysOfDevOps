1) **Core Components of Linux**

**Kernel (heart of Linux)**
Talks directly to hardware (CPU, memory, disk, network)
Responsibilities:
  Process scheduling
  Memory management
  Device drivers
  System calls (syscalls)
You don’t touch it daily, but everything runs through it

**User Space**
Where you live
Shells (bash), tools (ps, top, ls)
Applications (nginx, java, python)
User-space apps ask kernel to do work via syscalls

**Init System (systemd)**
First process started by kernel → PID 1
Brings the system up
Starts, stops, restarts services
Manages logs, services, targets (runlevels)

=======================================================================================================================================================================

2) **How Processes Are Created & Managed**

**Process creation flow**
A process calls fork() → child process created
Child calls exec() → loads new program
Kernel assigns:
     PID
     Memory space
     CPU scheduling

**Every process has**
    PID (Process ID)
    PPID (Parent PID)
    State
    Resource usage (CPU, RAM)
   
**Check via:**
ps -ef
ps aux

3) **Process States (VERY IMPORTANT)**
From man ps:
    R – Running
        Actively using CPU or ready to run
    S – Sleeping
        Waiting for I/O (disk, network)
        Normal for most services
    D – Uninterruptible Sleep
        Waiting on disk/network (cannot be killed)
        ⚠️ Red flag during hangs
    T – Stopped
        Paused (Ctrl+Z or debugger)
    Z – Zombie
        Process finished, parent didn’t clean it up
        Usually harmless, but too many = bad parent process

   ==================================================================================================================================================================

4) **What systemd Does (and Why It Matters)**
**systemd = service manager + init**
      Starts services in correct order
      Restarts crashed services
      Tracks service state
      Central logging via journald
**Commands:**
    systemctl status nginx (check status of the service)
    systemctl restart nginx (Restart the service)
    journalctl -u nginx (shows logs for a service)
   
=====================================================================================================================================================================

5) **5 Linux Commands You’ll Use Daily**
    **ps** → process inspection
    **top / htop** → live CPU & memory
    **systemctl** → service control
    **journalctl** → logs (better than /var/log)
    **free / df** → memory & disk health
   
