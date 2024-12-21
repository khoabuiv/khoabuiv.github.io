---
layout: post
---

### Package Management
- Biggest advantage of Linux enterprise systems. Features for package management: 
    - Automation: No need for manual installs and upgrades
    - Scalability: Install packages on one system, or 10,000 systems
    - Repeatability and predictability
    - Security and auditing
- What does package management do? 
    - Gather and compress associated software files into a single package 
    - Allow for easy software installation or removal
    - Can verify file integrity via an internal database
    - Can authenticate the origin of packages
    - Facilitate upgrades
    - Group packages by logical features
    - Manage dependencies between packages
- Package types:
    - **Binary Packages**: contain files ready for deployment, including executable files and libraries. These are architecture-dependent.
    - **Source Packages**: used to generate binary packages; one should always be able to rebuild a binary package from the source package. One source package can be used for multiple architectures.
    - **Architecture-Independent Packages**: contain files and scripts that run under script interpreters, documentation, and configuration files.
    - **Meta-Packages**: groups of associated packages that collect everything needed to install a relatively large subsystem, such as a desktop environment, or an office suite, etc.
- **Red Hat Package Manager(RPM)**: Used by Red Hat derived distributions like RHEL, Fedora, CentOS, SUSE. 

- **Debian Package(dpkg)**: Used by all Debian derived distributions. 
    - Package files have a **.deb** suffix and the DPKG database resides in **/var/lib/dpkg** directory.
    - Naming convention for a binary file: 
    <code> <name>_<version>-<revision_number>_<architecture>.deb </code>
    - List all packages installed: <br>
    <code> dpkg -l </code> <br>
    - List files installed in the package: <br>
    <code> dpkg -L {package} </code> <br>
    - Show a package's information: <br>
    <code> dpkg -s {package} </code> <br>
    - To install or upgrade a package: <br>
    <code> sudo dpkg -i {package} </code> <br>
    - To remove a package, but keep its config file: <br> 
    <code> sudo dpkg -r {package} </code> <br>
    - To remove a package including its config file: <br> 
    <code> sudo dpkg -P {package} </code> <br>
    - To find what package a file belongs to: <br>
    <code> dpkg -S {file_name} </code> <br>


