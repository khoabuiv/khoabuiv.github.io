---
layout: post
---

# I/O Management

## I/O Management Tools
- **iostat**: the basic workhorse utility for monitoring I/O device activity on the system. It can generate reports with a lot of information, with the precise content controlled by options. Example:
```
root@mariadb:~# iostat -xk
Linux 6.8.0-50-generic (mariadb) 	01/01/2025 	_x86_64_	(4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.02    1.70    0.08    0.00   97.95
```
- **iotop**: must be run as root. It displays a table of current I/O usage and updates periodically, like **top**.
- **I/O bound**: The CPU is idle while waiting for I/O tasks to finish 