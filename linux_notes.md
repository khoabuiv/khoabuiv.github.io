---
layout: default
---

## Linux Distributions:
- **Debian**: upstream for Ubuntu, Linux Mint, and others. Purely open source focus on stability. 
- **Red Hat**: CentOS Stream is very close to Red Hat Enterprise Linux. 
- OpenSUSE

## How to Setup sudo:
1. Use <code> su </code> to switch to root
2. Go to <code> /etc/sudoers.d </code>, edit the file using **visudo**, and add the line: <br>
<code> {username} ALL=(ALL:ALL) ALL </code><br>
The line has the following meaning: 
- {username} **ALL**=(ALL:ALL) ALL: Rule applies to all hosts
- {username} ALL=(**ALL**:ALL) ALL: The user can run commands as all users 
- {username} ALL=(ALL:**ALL**) ALL: The user can run commands as all groups 
- {username} ALL=(ALL:ALL) **ALL**: The rules are applied to all commands.  

3. Add the following to <code> PATH=$PATH:/usr/sbin:/sbin </code> to the <code> .bashrc </code> file in the home directory. 

## [Filesystem Tree Layout](https://khoabuiv.github.io/linux/filesystem_tree_layout.html)

## [User Environment](https://khoabuiv.github.io/linux/user_environment.html)

## [Account Management](https://khoabuiv.github.io/linux/linux_account_management.html)

## [Package Management](https://khoabuiv.github.io/linux/package_management.html)

## [Version Control with Git](https://khoabuiv.github.io/linux/git.html)

## [Programs in Linux](https://khoabuiv.github.io/linux/programs_in_linux.html)

## [Memory Management](https://khoabuiv.github.io/linux/memory_management.html)

## [I/O Management](https://khoabuiv.github.io/linux/io_management.html)

## [Containers](https://khoabuiv.github.io/linux/containers.html)

## [Disk Management](https://khoabuiv.github.io/linux//disk_management.html)

## [Kernel Management](https://khoabuiv.github.io/linux/kernel_management.html)

## [Network](https://khoabuiv.github.io/linux/network.html)

## Using Cron
- Be careful of the difference between system-wide cron(Runs by root) and user cron(run by users)
- Crontabs are at **/etc/crontab**

Cronline: 
```
* * * * * <command>
```
1: Minute
2: Hour
3: Day of the month
4: Month of the year
5: Day of the week
Use / to indicate repeat of every time interval.
To add a new cronjob. Run:
```
crontab <filename>
```

## 