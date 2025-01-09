---
layout: post
---
# Memory Management

## How to configure and manage swap space?
1. Create a swap file:
```
sudo dd if=/dev/zero of=/swapfile bs=1M count=1024
```
2. Set the file permission to 600:
```
sudo chmod 600 /swapfile
```
3. Make the file usable as swap space:
```
sudo mkswap /swapfile
```
4. Active the swap file:
```
sudo swapon /swapfile
```
5. To  deactive 

## Memory Monitoring Tools
- **free**: Brief summary of memory usage:
```
root@mariadb:~# free -m
               total        used        free      shared  buff/cache   available
Mem:            7751         863        5588          37        1299        6610
Swap:           2047           0        2047
```
- **vmstat**: Detailed virtual memory statistics and block I/O, dynamically updated
```
root@mariadb:~# vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0 5662600  51032 1286212    0    0   209    13  562  115  0  2 97  0  0
```
- **pmap**: Process memory map
Also consult **/proc/meminfo**:
```
root@mariadb:~# cat /proc/meminfo
MemTotal:        7937852 kB
MemFree:         5722384 kB
MemAvailable:    6768956 kB
```

## Tuning Memory
The **/proc/sys/vm** directory contains many tunable knobs to control the Virtual Memory system. The value can be change directly or using the **sysctl** utility. The primary tasks are:
    - Controlling how many pages are allowed to be dirty and how often they are flushed out to disk.
    - Controlling how much pages that reflect file contents are allowed to remain in memory, as opposed to those that need to be swapped out as they have no other backing store.
    - Controlling how much memory overcommission is allowed, since many programs never need the full amount of memory they request.

## Swap Usage
Linux uses a virutal memory system in which the OS can functoin as if it had more memory than it does:
    - Many programs do not actually use all the memory they are given permission to use. 
    - When memory pressure becomes important, less active memory regions may be swapped out to disk, to be recalled only when needed again.
- **mkswap**: format swap partitions or files
- **swapon**: activate swap partitions or files
- **swapoff**: deactivate swap partitions or files


## OOM Killer
One can modify and even turn off overcommission by setting the value of **/proc/sys/vm/overcommit_memory**:
    - **0**: Permit overcommission, but refuse obvious overcommits, and give root users somewhat more memory allocation than normal users.
    - **1**: All memory requests are allowed to overcommit.
    - **2**: Turn off overcommission. Memory requests will fail when the total memory commit reaches the size of the swap space plus a configurable percentage (50 by default) of RAM. This factor is modified changing /proc/sys/vm/overcommit_ ratio.

