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
- **Directory Tree**: <br>
| Directory      | Purpose      |
| ------------- | ------------- |
| / | Primary directory of the entire filesystem hierarchy |
| /bin | Essential executable programs that must be available in **single user mode** |
| /boot | Files needed to boot the system, such as the kernel, **initrd** or **initramfs** images, and boot configuration files and bootloader programs |
| /dev | Device Nodes, used to interact with hardware and software devices |
| /etc | System-wide configuration files |
| /home | User home directories, including personal settings, files, etc. |
| /lib | Libraries required by executable binaries in /bin and /sbin | 
| /lib64 | 64-bit libraries required by executable binaries in /bin and /sbin, for systems which can run both 32-bit and 64-bit programs |
| /media | Mount points for removable media such as CDs, DVDs, USB sticks, etc. |
| /mnt | Temporarily mounted filesystems | 
| /opt | Optional application software packages |
| /proc | Virtual pseudo-filesystem giving information about the system and processes running on it. Can be used to alter system parameters. |
| /run | Run-time variable data, containing information describing the system since it was booted. Replaces the older /var/run |
| /sys | Virtual pseudo-filesystem giving information about the system and processes running on it. Can be used to alter system parameters. Similar to a device tree and is part of the Unified Device Model. |
| /root | Home directory for the root user |
| /sbin | Essential system binaries |
| /srv | Site-specific data served up by the system. Seldom used. |
| /tmp | Temporary files; on many distributions lost across a reboot and may be a ramdisk in memory. |
| /usr | Multi-user applications, utilities and data; theoretically read-only. | 
| /var | Variable data that changes during system operation |
| /misc | (Optional) can be used for miscellaneous data |
| /tftpboot | used for booting using **tftp** | 