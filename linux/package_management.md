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
- **[Red Hat Package Manager(RPM)](https://khoabuiv.github.io/linux/rpm.html)**: Used by Red Hat derived distributions like RHEL, Fedora, CentOS, SUSE. 
- **[dnf](https://khoabuiv.github.io/linux/dnf.html)**: Front end to RPM, but also has capabilities to retrieve packages from one or more remote repositories. 
- **[Debian Package(dpkg)](https://khoabuiv.github.io/linux/dpkg.html)**: Used by all Debian derived distributions. 
- **[APT(Advanced Packaging Tool)](https://khoabuiv.github.io/linux/apt.html)**: a set of programs provide a higher level of intelligent services for using the underlying dpkg program, and plays the same role as dnf on Red Hat-based systems.