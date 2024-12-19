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

## [Filesystem Tree Layout](https://khoabuiv.github.io/filesystem_tree_layout.html)

## [User Environment](https://khoabuiv.github.io/user_environment.html)

## [Account Management](https://khoabuiv.github.io/linux_account_management.html)