---
layout: post
---

## What's a process?
- Linux creates a new process for every program that is executed or run.
- Every process has a **pid** (Process ID), a **ppid** (Parent Process ID), and a **pgid** (Process Group ID). 
- Largest PID has been limited to a 16-bit number, or 32768.
- It is possible to alter this value by changing **/proc/sys/kernel/pid_max**. As processes are created, eventually they will reach pid_max, at which point they will start again at PID = 300.
- **Multi-threading**: Each thread of a program can be considered its own process.
- All processes have the following attributes: 
    - The program being executed
    - Context (state): the snapshot at any given time by recording the state of CPU registers, where it is executing in the program, what is in the process' memory, and other information.
    - Permissions
    - Associated resources
- **setuid**: Programs which are marked with an ”s” execute bit have a different ”effective” user id than their ”real” user id. **setuid** owns by root can cause security problem.
- **System calls**: processes don't have direct access to the hardware. Hardware is managed by the kernel which uses **system calls** to indirectly access hardware. 

## Control processes' limits
- **ulimit** is a built-in bash command that displays or resets process resource limits. 
    - Setting limits:
    ```
    ulimit [options] [limit]
    ```
    This would only affects the current shell. To make changes that are effective for all logged-in users, you need to modify **/etc/security/limits.conf** and then reboot.
    - **Hard limit**: The maximum value, set only by the root user, that a user can raise the resource limit to.
    - **Soft limit**: The current limiting value, which a user can modify, but cannot exceed the hard limit.

## Managing processes
- **forking**: The original parent process keeps running, while the new child process starts.
- **exec**: Where the parent process terminates, and the child process inherits the process ID of the parent.
- **background processing**: Parent shell skips the wait request and is free to issue a new shell prompt immediately, allowing the background process to execute in parallel.
    - Activates by **&** at the end of the command line. For example: 
    ```
    sudo updatedb &
    ```
    **CTRL-Z** suspends a foreground process. **bg** makes it run in the background. **fg** puts it in the foreground. **CTRL-C** terminates a foreground process.
- **foreground requests**: The shell waits until the child process has completed or is stopped via a signal.
- The **jobs** command shows background processes in the current terminal. 
- **at** executes any any non-interactive command at a specified time. For example: 
```
warning: commands will be executed using /bin/sh
at Thu Jan  2 04:58:00 2025
at> echo "2 days later"
at> <EOT>
job 1 at Thu Jan  2 04:58:00 2025
```
Use **CTRL-D** to insert the EOT character.
- **cron** is used for any job that needs to run on a regular schedule, scheduling commands at specific intervals. Tasks can be queued to run every hour, every day, once a week or once a month, or even every 10 seconds. 
- Managing cron: 
    - **crontab** lets users specify jobs
    - /etc/cron.d/ can be extended with formatted job files
    - /etc/cron.{hourly,daily,weekly,monthly} can contain any system script
- **sleep**: causes the calling thread to sleep either until the number of real-time seconds specified in seconds
- Process states: 
    - **Running**: A process is currently receiving attention from the CPU (in other words, executing) or waiting in a queue ready to run. 
    - **Sleeping**: A process is waiting on a request that it has made (usually I/O) and cannot proceed further until the request is completed.
    - **Stopped**: Meaning execution of instructions has been suspended.
    - **Zombie**: is entered when a process terminates. Zombie processes are important, because each Zombie continues to take up space in the O/S’s process table.
- There are two execution modes: **user mode** and **system mode**. 
    - Except when executing a system call, processes execute in user mode, where they have lesser privileges than in the kernel mode.
    - **Process resource isolation**: When a process is started, it is isolated in its own user space to protect it from other processes.
    - Application code never runs in kernel mode, only the system call itself which is kernel code. 
- **Daemons**: is a background process whose sole purpose is to provide some specific service to users of the system.
- Process priority can be controlled through the **nice** and **renice** commands. 
    - **nice** can raise or lower a process’ priority by adjusting its nice value.
    - **renice** is used to raise or lower the nice value of an already running process. 
    - Higher nice values lower the priority.
    - Lower nice values raise the priority.
    - Nice value can range from -20 (lowest nice, highest priority) to +19 (highest nice, lowest priority).
    - Only the superuser can lower a nice value but any user can raise their process’ nice value. 
    - If you do not give a nice value, the default is to increase the niceness by 10. 


## Monitoring processes
- Built-in tools to monitor processes:
    - **top**: Process activity, dynamically updated
    - **uptime**: How long the system is running and the average load
    - **ps**: Detailed information about processes. Example usage:
    ```
    root@mariadb:~# ps -o pid,user,uid,priority,cputime,pmem,size,command
    PID USER       UID PRI     TIME %MEM  SIZE COMMAND
    3575 root         0  20 00:00:00  0.0  1284 sudo su -
    3576 root         0  20 00:00:00  0.0   804 su -
    3577 root         0  20 00:00:00  0.0  1720 -bash
    3620 root         0  20 00:00:00  0.0  1100 ps -o pid,user,uid,priority,cputi
    ```
    - **pstree**: A tree    - **mpstat**: Multiple processor usage
    - **iostat**: CPU utilization and I/O statistics
    - **sar**: Display and collect information about system activity
 of processes and their connections
    - **numastat**: Information about NUMA (Non-Uniform Memory Architecture)
    - **strace**: Information about all system calls a process makes
**/proc** contains a subdirectory for each active process, named by the process id (PID). **/proc/self** is the currently executing process. 

## Troubleshooting Technigues
Steps to procedurally troubleshoot:
    - Characterize the problem
    - Reproduce the problem
    - Do the easy things first
    - Eliminate possible causes one at a time
    - Change only one thing at a time; if that does not fix the problem, change it back
    - Check the system logs (/var/log/messages, /var/log/secure, etc.) for further information

