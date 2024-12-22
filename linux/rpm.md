---
layout: post
---
## Red Hat Package Manager(RPM)
- RPM naming format for a binary package is: <br>
<code> {name}-{version}-{release}.{distro}.{architecture}.rpm </code> <br>
Source package is: <br>
<code> {name}-{version}-{release}.{distro}.src.rpm </code> <br>
- **/var/lib/rpm** is the system dirtectory that holds the RPM database files. Can be modify with **--dbpath**. Database can be rebuilt with: <code> sudo rpm --rebuilddb </code>

- All rpm queries comes with the **-q** option as follow:
    - Find version of a package installed: <code> rpm -q {package} </code>
    - Find package that the file come from: <code> rpm -qf {file} </code>
    - Find files were installed by a package: <code> rpm -ql {package} </code>
    - Show information about the package: <code> rpm -qi {package} </code>
    - List all installed packages: <code> rpm -qa </code>
    - **--requires** return a list of prerequisites for a package.
    - **--whatprovides** show what installed package provides a particular reuisite package. 
    - To verify a package: <code> rpm -V {package} </code>. If it's none then nothing been change, output indicates size, checksum, and modification time have changed. 
    - To install a package: <code> rpm -i {package} </code>
    - To uninstall a package: <code> sudo rpm -e {package} </code>
    - To update a package: <code> rpm -U {packge} </code>. To downgrade, add **--oldpackage** option to the commandline. 
    - To freshen a package: <code> rpm -F {package} </code>. Useful for when downloaded new patches and want to upgrade the packages that are already installed, but not install any new ones.
    - To install a new kernel on a Red Hat-based system: <code> sudo rpm -ivh kernel-{version}.{arch}.rpm </code>. This will require a reboot. 
    - **rpm2archive** is use to convert RPM packages files to **tar** archives. 

