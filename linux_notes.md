---
title: Home
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

## Filesystem Tree Layout:
- Linux consists of one big logical filesystem tree. 
- There maybe be many distinct filesystems mounted to the system at various points appearing as subdirectories. 
- **Shareable data**: data that can be shared between hosts.
- **Non-shareable data**: data belongs exclusively to one host.
- **Static data**: binaries, libraries, documentations, and anything that does not change without sys-admin making the changes.
- **Variable data**: anything that maybe change, even without sys-admin making changes.   
- **Filesystem Hierarchy Standard(FHS)**: specifies the main directories that need to be present, and describes their purposes. 
- **Directory Tree**: Use Quizlet [link](https://quizlet.com/ca/987238091/fhs-linux-standard-directory-tree-flash-cards/) to practice. 
- **Root Directory(/)**: Must contain all essential files required to boot the system and then mount all other filesystems. Root directory must have the files to:
    - Boot the system.
    - Restore the system from backups on external media.
    - Recover and/or repair the system. 
**Note**: no application or package should create new subdirectories of the root directory.

- **/bin Directory**: Important for the following: 
    - Contains executable programs and scripts needed by users which are required when no other filesystems have yet been mounted. 
    - Contains executable used indirectly by scripts.
    - May not include any subdirectories.
**/usr/bin** are for binaries that are required only by non-root users. 

- **/boot Directory**: Contains everything required for the boot process. The following files are essential:
    - **vmlinuz**: The compressed Linux kernel
    - **initramfs**: The initial RAM filesystem, mounted before the real root filesystem becomes available. Can also be **initrd**
Also includes the following files for debugging:
    - **config**: Used to configure the kernel compilation.
    - **System.map**: Kernel symbol table, used for debugging. 

- **/dev Directory**: contains **special device files** which represent devices built into or connected to the system.
