---
layout: post
---

### How to change the default shell for an user?
```
sudo usermod <username> -s "/usr/bin/<shell>"
```

### Why use different user accounts?
- Security reasons, avoid admin mistakes, specific user to run specific processes. 

### Atributes of an user account
- Each user has a corresponding line in the **/etc/passwd** file
- Attributes of an user account:
    - **Username**: Unique name assigned to each user.
    - **Password**: Password assigned to each user.
    - **User Identification Number(UID)**: An unique number assigned to the user account. 
    - **Group Identification Number(GID)**: An unique number assigned to the group of users. 
    - **Comment or GECOS information**: A defined method to use the comment field for contact information. 
    - **Home Directory**: An unique directory that offers a working area for the user. Can be found under **/home**
    - **Login shell**: Shell program such as **/bin/bash** or **/bin/csh**.
    
### How to determine the current user? 
- <code> whoami </code> shows the current username.
- <code> who </code> shows the users logged in the system.
- <code> id </code> shows the current user ID, group ID, and numeric version. 

### Startup Files
- Startup files are included with a new shell to ensure its proper functioning. Including:
    - Defining relevant environment variables.
    - Defining alias that are used as shorthand.
    - Defining functions. 

- System-wide initializing files found in **/etc**. 
- Files in the user home directory override global settings. 
- Why use startup files?
    - Customization
    - Setting terminal type
    - Setting shortcuts and aliases
    - Setting default text editor. 

- Startup files order: 
    1. **/etc/profile**: is read and evaluated first.
    2. **~/.bash_profile**: login shells configuration.
    3. **~/.bash_login**: login initialization.
    4. **~/.profile** overrides **/etc/profile**
Majority of customizations should go into **~/.bashrc**. 

### Adding new users:
- Use the command <code> sudo useradd {username} </code>. Which causes the following steps: 
    1. The next **UID** greater than **UID_MIN**, defined in **/etc/login.defs**, is assigned as the new user's UID.
    2. A group is created where **GID=UID** and assigned as the new user's primary group.
    3. A home directory is created at **/home/{username}** and set ownership to the new user.
    4. **/bin/bash** will be set as the default home directory.
    5. The contents of **/etc/skel** is copied to **/home/{username}**. By default, the contents including startup files for bash and X Window system.
    6. An entry of **!!** is placed in the password field of the **/etc/shadow** for the new user's entry, requiring the admin to assign a password for the account to be usable. 

### Deleting an user:
- Use the command <code> sudo userdel {username} </code>. This causes all the references to the user to be erased from **/etc/passwd**, **/etc/shadow**, and **/etc/group**. The home directory is preserved, use flag **-r** to over-write this. 

### Modify an user:
- Use the command <code> usermode {username} </code> to modify the user account group memberships, home directory, login name, password, default shell, etc. 

### Locked Accounts:
- Accounts that can run programs, but can never login to the system and does not have a valid password. They are marked as follow in the **/etc/passwd** file: <br>
<code> bin:x:1:1:bin:/bin:/sbin/nologin  </code> <br>
Message to return if a locked user try to login can be modified at **/etc/nologin.txt**. Locked accounts have no valid password and represented as **!!** in **/etc/shadow**.

### User IDs and Password Management:
- Normal user accounts start at 1000, less than 100 is reserved for the system. 
- **/etc/passwd** file contains one line for each user, each of which is a colon(:) seperated list of fields.
    - Username
    - Password
    - UID
    - GID
    - Comment
    - Home
    - Shell
It is bad practice to edit **/etc/passwd**, **/etc/group**, or **/etc/shadow** directly. Use <code> usermod </code> or tools like **vipw/vigr** instead. 

- **/etc/passwd** has the (-rw-r--r--) permission. **/etc/shadow** should be used since it has 400 permission making it more difficult to collect the hashed password. 
- Format of the **/etc/shadow** file is as follow with each fields seperated by colons(:): 
    - **username**: unique user name
    - **password**: the hashed (sha512) value of the password
    - **lastchange**: days since Jan 1, 1970 that password was last changed
    - **mindays**: minimum days before password can be changed
    - **maxdays**: maximum days after which password must be changed
    - **warn**: days before password expires that the user is warned
    - **grace**: days after password expires that account is disabled
    - **expire**: date that account is/will be disabled
    - **reserved**: reserved field
The username in each record must match exactly that found in **/etc/passwd**

#### Changing Password
- To change password: <code> passwd </code>
- Password choice is examined by **pam_cracklib.so** to reject bad passwords. 

#### Password Aging
- Password can have a TTL set by <code> chage [-m mindays] [-M maxdays] [-d lastday] [-I inactive] [-E expiredate] [-W warndays] {username} </code>
- To force user to change password the next time they log in: <code> sudo chage -d 0 {username} </code>

### Managing Root Account:
#### How to grant root access?
```
sudo visudo
>> <username> ALL=(ALL) NOPASSWD:ALL 	
```
Where the format is as follow:
```
user hosts=(users:groups) commands
```

- **sudo** allow regular user accounts to switch to root or other user. Access to **sudo** can be configure in **/etc/sudoers** and **/etc/sudoers.d**.
- **su** creates a sub-shell that allows user to elevated privileges until they exit that shell.
- We have SSH to manage root access across a network. SSH is configure with **/etc/ssh/sshd_config**, and PAM through **pam_securetty.so** associated with **/etc/securetty** which manages which devices can connect. 
- Use **pssh** utility to execute a command on multiple systems. For example: <br>
<code>
$ for machines in node1 node2 node3
  do
      (ssh $machines some_command &)
done
</code>
or 
<code> pssh -viH machine1 machine2 machine3 do_something </code>

- To transfer file, use **scp**: 
<code>
$ scp file.txt farflung.com:/tmp
$ scp file.tex student@farflung.com/home/student
$ scp -r some_dir farflung.com:/tmp/some_dir
</code>

- SSH order of configuration files:
    1. Command line options
    2. **~/.ssh/config**
    3. **/etc/ssh/ssh_config**

#### Remote Graphical Login
- Full graphical desktop using VNC(Virtual Network Computing)
- Implementation with **tigervnc**


### Group Management
- **Group**: A collection of users. 
- Groups are defined in **/etc/group** with this format: <code> groupname:password:GID:user1,user2,... </code> where user is comma seperated. Group password can be set only if **/etc/gshadow** exists. 
- An user has one primary group, and between 0 and 15 secondary groups. 
- Group management with these commands:
    - **groupadd**: Add a new group.
    - **groupmod**: Modify a group's attribute.
    - **groupdel**: Remove a group.
    - **usermod**: Manage an user's group membership. 

### File Management and Ownership
- **umask**: Shows the current default setting. 
    - Can be show with <code> umask -S </code>
    - Modify with: <code> umask u=r, g=rw, o=rwx </code>
- **Filesystem Access Control List(ACLs)**: extend the simpler user, group, and world system. Using **getfacl/setfacl**
