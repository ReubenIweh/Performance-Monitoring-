# Performance-Monitoring-
Performance monitoring is the process of continuously observing and analyzing system resource usage to maintain optimal performance, detect issues early, and troubleshoot problems effectively. It helps system administrators,and developers understand how applications and services interact with system resources such as CPU, memory, disk, and network. This is to ensures the system runs efficiently and reliably.


![Install MySQL Screenshot](./image01.png)


 📑 **Table of Contents**
 
- [CPU Usage](#cpu-usage)
- [Memory Usage](#memory-usage)
- [Disk I/O](#disk-i/o)
- [Storage Usage](#storage-usage)
- [Network Activity](#network-activity)
- [Processes](#processes)
- [Observation Tools Readings](#observation-tools-readings)


**Below are the critical areas to monitor and the tools commonly used to track them.**


## CPU Usage

Monitor CPU load to identify system stress or misbehaving processes.

Commands: `top`, `htop`, `mpstat`, `vmstat` `sar`, `vmstat`,   `mstat`

What to Watch: High user/system % usage, load average, and CPU steal time (in virtualized environments)

## Memory Usage

Keep an eye on RAM and swap usage to prevent performance degradation.

Commands: `free -h`, `top`, `vmstat`

Key Metrics: Used/free memory, swap usage, cached memory

## Disk I/O

Disk I/O bottlenecks can slow down your applications significantly.

Commands: `iostat`, `iotop`, `dstat`

Metrics: Read/write speed, IOPS, wait time, and utilization

## Storage Usage

Avoid crashes and data loss by ensuring sufficient disk space.

Commands: `df -h`, `du -sh`, `lsblk`

Metrics: Disk usage per partition, inode usage

## Network Activity

Monitor bandwidth and network errors to diagnose connectivity issues.

Commands: `ip -s link`, `ss`, `netstat`, `iftop`, `nload`, `sar`

Metrics: Packets sent/received, errors, dropped packets, bandwidth

## Processes

dentify resource-hungry or zombie processes affecting system performance.

Commands: `top`, `ps aux`, `htop` `pidstat`

Focus Areas: CPU/memory usage by process, process state, run-time

## Observation Tools Readings

**vmstat**

![Install vmstat](./images/vmstat.png)

- r: Number of processes running on CPU, value greater than the CPU count is “saturation”.
- free: Free memory in kilobytes.
- si, so: Swap-in and swap-out. If these are non-zero, you’re probably out of memory “saturation” .
- us, sy, id, wa, st: the breakdown of CPU time, on average across all CPUs. They are user time, system time (kernel), idle, wait I/O, and stolen time (by other guests).
- In above example, CPU time is almost entirely in user-level, pointing to application level usage .

**mpstat**

![Install mpstat](./images/mpstat.png)

- Shows CPU time breakdown per CPU, can be used to check for an imbalance.
A single hot CPU could mean a single-threaded application for example.

**htop**

![Install htop](./images/htop.png)

CPU Bars: Show usage per core.

Memory:

Don’t panic if it looks "full"  cached memory is reusable.

Swap: Used when RAM is full high swap usage = potential memory pressure.

Load Avg: 1, 5, and 15-minute system load.

Compare to CPU cores (e.g., load > 4 on a 4-core VM = overloaded).

Tasks: Shows total processes and threads.

Running = actively using CPU.

Per-Process Info:

%CPU, %MEM: Resource usage

PID, USER, COMMAND: Identify the process

S: State (R = running, S = sleeping)

Use F6 to sort, F3 to search, F9 to kill a proces

**free**

![Install free](./images/free.png)

- total: 1.7Gi: Total physical RAM available.

- used: 207Mi: Memory actively in use (excluding cache and buffers).

- free: 1.0Gi: Completely unused memory.

- shared: 8.0Mi: Memory used by tmpfs and shared between processes.

- buff/cache: 511Mi: Memory used by the kernel for buffers and cache (reclaimable).

- available: 1.4Gi: Estimation of memory available for new applications, accounting for reclaimable cache.

**iostat**

  ![Install free](./images/iostat.png)

- r/s, w/s, rkB/s, wkB/s: These are the delivered reads, writes, read Kbytes, and write Kbytes per second to the device. A performance problem may simply be due to an excessive IO load.
  
- await: The average time for the I/O in milliseconds. This is the time that the application suffers, as it includes both time queued and time being serviced.
  
- High values can be an indicator of device “saturation” or device problems.
  
- avgqu-sz: The average number of requests issued to the device. Values greater than 1 can be evidence of “saturation” (although devices can process in parallel
