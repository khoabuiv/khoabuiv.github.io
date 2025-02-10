---
layout: post
---

### Essential Commands: 
- **mount**: Gives an overview of all mounted devices.
- **findmnt**: Shows mounts and the relationship that exists between the different mounts.
- **df**: Shows available disk space on mounted devices.

### General Notes:
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

### Environment Configuration Files:
- **/etc/profile**: This is the generic file that is processed by all users upon login.
- **/etc/bashrc**: This file is processed when subshells are started.
- **~/.bash_profile**: In this file, user-specific login shell variables can be defined.
- **~/.bashrc**: In this user-specific file, subshell variables can be defined.



### Essential Directories: 
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

- **/dev Directory**: Contains **special device files** which represent devices built into or connected to the system. The files represent byte-stream and block I/O devices

- **/etc Directory**: Contains machine-local configuration files and some startup scripts. Should not contain executable binary programs. It has the following important subdirectories:
    - **/etc/skel**: Contains **skeleton** files used to populate newly created home directories.
    - **/etc/sysstemd**: Contains or points to configuration scripts for starting, stopping, and controlling system services when using systemd
    - **/etc/init.d**: Contains startup and shutdown scripts for when using System V initialization.

- **/home Directory**: All personal, configuration, data, and executable progarams are placed under this directory. Subdirectories contain content for various groups and users. You can use <code>$HOME</code> or <code>~</code> to get to an user's home directory. 

- **/lib and /lib64 Directories**: Contain libarries needed to execute the binaries in /bin and /sbin. These libaries are used for booting system and executing commands within root filesystem.
**Note**: Some newer distributions just have one directory for lib and use symbolic links to preserve the two directories view. 

- **/media Directory**: Used to mount filesystems on removable media. 

- **/mnt Directory**: Use for temporarily mount a filesystem. Use for network filesystems like: NFS; Samba; CIFS; AFS.

- **/opt Directory**: Designed for software packages that wish to keep all or most of their files in one isolated place. Directories: **/opt/bin**, **/opt/doc**, **/opt/include**, **/opt/info**, **/opt/lib**, and **/opt/man** are reserved for local sys-admin use. 

- **/proc Directory**: The mount point for pseudo-filesystem, where all information resides only in memory and not disk. The entries are considered to be **virtual files** which can be listed as zero bytes, but contain large amount of information. <br>
**Note**: Important pseudo-files: **/proc/interrupts**, **/proc/meminfo**, **/proc/mounts**, **/proc/partitions**, **/proc/filesystems**. and **/proc/sys/**.
    - **/proc/scsi/** contains information for all physical SCSI devices. Likewise, the **process directories** contain information about each running process on the system.

- **/sys Directory**: The mount point for the **sysfs** pseudo-filesystem where all information resides only in memory. Empty for non-running system. **sysfs** is used to gather information about the system, and modify its behavior while running. 

- **/root Directory**: Home directory for root user. 

- **/sbin Directory**: Contains binaries essential for booting, restoring, recovering, and/or repairing to those in /bin directory.

- **/srv Directory**: Contains site-specific data served by the system. Ubuntu and Red Hat has **/srv** empty by default. 

- **/tmp Directory**: Used to store temporary files, and can be accessed by any other user or application. Avoid creating large files on **/tmp** as they occupy space in memory rather than disk. 
- To cancel policy for storing **/tmp** on disk, run: <br>
<code> sudo systemctl mask tmp.mount </code> <br>
Then follow by a system reboot. 

- **/usr Directory**: Can be thought of as a secondary hierarchy. Used for files not needed for system booting. Does not need to reside in the same partition as the root directory, and can be shared across a network. Software packages should not create subdirectories under **/usr**. Use symbolic links to other locations for compability. Typically only contains read-only data

- **/var Directory**: Contaions variable data files that change frequently during system operation. These includes: log files; spool directories and files; administrative data files; temporary files such as cache contents. <br>
**Note**: best practice to mount **/var** as a separate filesystem. **/var/spool** is for local files for processes such as mail, printing, and cronjobs. 

- **/run Directory**: Store **transient files**, files that contain runtime information. Generally implemented as an empty mount point, with a tmpfs ram disk (like **/dev/shm**) mounted there at runtime. 

- <code> sudo du -shxc --exclude=proc * </code> to show data usage of the directories. 

- Directories that contain special entries which abstract system properties, instead of data stored on the disk: **/dev**; **/proc**; **/sys**. 