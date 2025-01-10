---
layout: post
---
# Filesystem Basics
- **inode**: a data structure on disk that describes and stores file attributes, such as:
    - Permissions​
    - User and group ownership​
    - Size​
    - Timestamps (nanosecond)
        - ​Access time 
        - Modification time
        - Change time.
Filenames are stored in the directory, not the inode. 

## LVM Storage management
- There are three components of LVM: Physical; Volume; Logical.
- How to view the block device? **lsblk, pvsm, vgs**
- To reduce a VG: 
```
sudo vgreduce <volume name> <filesystem>
```
- To add a new VG: 
```
vgcreate <volume name> <filesystem>
```
- To create a new LV for a VG: 
```
sudo lvcreate --size <size> --name <directory 1> ... <directory n> 
```
This is stored on **/dev/directory_1/.../directory_n**

## How to format a disk?
Use mkfs as follow
```
sudo mkfs -t <filesystem_type> <disk_name>
```


## How to mount a VFS?
1. Mount the filesystem to the directory:
```
mount <filesystem> <directory>
```
2. Vice versa, you can unmount with:
```
umount <filesystem>
```

## How to configure auto-mount?
1. Edit the fstab file with **noauto** option. Example:
```
UUID=8d113aa7-30d8-4c6d-b012-eeea1c463312   /backup    ext4   noauto,defaults    0 0
```


## How to make a mount read only?
1. Run the command:
```
mount -o ro <filesystem> <directory>
```

## /etc/fstab
Each record in the /etc/fstab file contains information about a filesystem to be mounted at boot, their standard mount points and what options should be used when mounting them. Each record in the file contains white space separated fields of information about a filesystem to be mounted:
- Device file name (such as /dev/sda1), label, or UUID
- Mount point for the filesystem (where in the tree structure is it to be inserted)
- Filesystem type
- A comma-separated list of options
- dump frequency used by the dump -w command, or a zero which is ignored by dump
- fsck pass number or a zero - meaning do not fsck this partition
The mount and umount utilities can use information in /etc/fstab.

## Links
- **Hard links**: points to an inode.​ They are made by using **ln**. Two or more files can point to the same inode. All hard linked files have to be on the same filesystem. Changing the content of a hard linked file in one place may not change it in other places.
- **Soft links**: aka symbolic. They are made by using **ln -s**. Soft linked files may be on different filesystems. If the target does not yet exist or is not yet mounted, it can be dangling.
Badly written applications that can copy a file and change it and then replace it, or delete a file and replace it, and in the process create a new file that is not linked any more.
- **nodev** indicates special filesystems which do not reside on storage. 

## Notable Filesystems:
- **ext4**: Linux native filesystem 
- **XFS**: A high-performance filesystem originally created by SGI
- **JFS**: A high-performance filesystem originally created by IBM
- FAT12, FAT16, FAT32, VFAT, NTFS are windows-natives.
- proc, sysfs, devfs, debugfs are pseudo-filesystems resident only in memory.
- NFS, coda, afs are network filesystems.

- **journaling**: Operations are grouped into transactions. A transaction must be completed without error, atomically; otherwise, the filesystem is not changed. Thus help with recovering from system crashes with little or no corruption.
- Files have flags that can be set with **chattr** and view with **lsattr**. Available flags:
    - i: Immutable
    - a: Append-only
    - d: No-dump
    - A: No atime update
- Each filesystem type has its own particular formatting options and its own **mkfs** program. For example:
```
root@mariadb:~# ls -lhF /sbin/mkfs*
-rwxr-xr-x 1 root root 15K Apr  9  2024 /sbin/mkfs*
-rwxr-xr-x 1 root root 23K Apr  9  2024 /sbin/mkfs.bfs*
-rwxr-xr-x 1 root root 35K Apr  9  2024 /sbin/mkfs.cramfs*
lrwxrwxrwx 1 root root   6 Oct  8  2023 /sbin/mkfs.ext2 -> mke2fs*
lrwxrwxrwx 1 root root   6 Oct  8  2023 /sbin/mkfs.ext3 -> mke2fs*
lrwxrwxrwx 1 root root   6 Oct  8  2023 /sbin/mkfs.ext4 -> mke2fs*
-rwxr-xr-x 1 root root 51K Mar 23  2022 /sbin/mkfs.fat*
-rwxr-xr-x 1 root root 43K Apr  9  2024 /sbin/mkfs.minix*
lrwxrwxrwx 1 root root   8 Dec 20 21:14 /sbin/mkfs.msdos -> mkfs.fat*
lrwxrwxrwx 1 root root   6 Dec 20 21:14 /sbin/mkfs.ntfs -> mkntfs*
lrwxrwxrwx 1 root root   8 Dec 20 21:14 /sbin/mkfs.vfat -> mkfs.fat*
```

---
layout: post
---

- **SSD (Solid State Drive)**
- **HDD (Hard Disk Drive)** 
- **fdisk**: cli utility for disk partitioning. 

## Disk Partition
- Two common partition schemes: MBR (Master Boot Record); GPT (GUID Partition Table).
- GPT: May have up to 128 primary partitions. When using the GPT scheme, there is no need for extended partitions. Partitions can be up to 233 TB in.
- **blkid**: is an utility to locate block devices and report on their attributes. Example: 
```
root@mariadb:~# blkid /dev/sda*
/dev/sda: PTUUID="86eabe20-5bae-4421-b44d-5f868db10ea2" PTTYPE="gpt"
/dev/sda1: PARTUUID="c93cde54-cae8-4a4f-a714-2ccf57c1be63"
/dev/sda2: UUID="06F1-6200" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f8c6001d-84e9-49e3-ad67-2eb6f9feeacf"
/dev/sda3: UUID="19c5ce25-a085-434c-8ae2-bbb8be11756d" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="7ba971f7-262f-4a90-ad98-d1763afbb81e"
```
- **lsblk**: Presents block device information in a tree format.
- **dd**: Can be used for converting and copying files. For GPT systems, use **sgdisk** instead. 
- **fdisk**: A menu-driven partition table editor. It is the most standard and one of the most flexible of the partition table editors. **gdisk** is equivalent for GPT
- **sfdisk**: Is a non-interactive Linux-based partition editor program, making it useful for scripting. **sgdisk** is equivalent for GPT.
- **parted** is the GNU partition manipulation program. **gparted** is the GUI interface to parted. 

