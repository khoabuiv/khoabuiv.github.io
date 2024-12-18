---
layout: post
---
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




