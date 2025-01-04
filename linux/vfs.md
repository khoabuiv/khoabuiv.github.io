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

