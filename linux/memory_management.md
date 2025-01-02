---
layout: post
---

## Memory monitoring tools:
- **free**: Brief summary of memory usage:
```
root@mariadb:~# free -m
               total        used        free      shared  buff/cache   available
Mem:            7751         863        5588          37        1299        6610
Swap:           2047           0        2047
```
- **vmstat**: Detailed virtual memory statistics and block I/O, dynamically updated
- **pmap**: Process memory map
Also consult **/proc/meminfo**:
```
root@mariadb:~# cat /proc/meminfo
MemTotal:        7937852 kB
MemFree:         5722384 kB
MemAvailable:    6768956 kB

```
