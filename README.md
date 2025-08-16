# Performance-Monitoring-
Performance monitoring involves tracking key system metrics to understand resource utilization, identify bottlenecks, and ensure stable and efficient operation. Various command-line tools and utilities are available for this purpose.


![Install MySQL Screenshot](./image01.png)


 📑 **Table of Contents**
 
- [CPU Usage](#cpu-usage)
- [Memory Usage](#memory-usage)
- [Disk I/O](#disk-i/o)
- [Storage Usage](#storage-usage)
- [Network Activity](#network-activity)
- [Processes](#processes)
- [Observation Tools Readings](#observation-tools-readings)


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



