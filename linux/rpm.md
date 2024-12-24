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
    - Find version of a package installed: <br> <code> rpm -q {package} </code> <br>
    - Find package that the file come from: <br> <code> rpm -qf {file} </code> <br>
    - Find files were installed by a package: <br> <code> rpm -ql {package} </code> <br>
    - Show information about the package: <br> <code> rpm -qi {package} </code> <br>
    - List all installed packages: <br> <code> rpm -qa </code> <br>
    - **--requires** return a list of prerequisites for a package.
    - **--whatprovides** show what installed package provides a particular reuisite package. 
    - To verify a package: <br> <code> rpm -V {package} </code> <br>. If it's none then nothing been change, output indicates size, checksum, and modification time have changed. 
    - To install a package: <br> <code> rpm -i {package} </code> <br>
    - To uninstall a package: <br> <code> sudo rpm -e {package} </code> <br>
    - To update a package: <br> <code> rpm -U {packge} </code> <br> To downgrade, add **--oldpackage** option to the commandline. 
    - To freshen a package: <br> <code> rpm -F {package} </code> <br> Useful for when downloaded new patches and want to upgrade the packages that are already installed, but not install any new ones.
    - To install a new kernel on a Red Hat-based system: <br> <code> sudo rpm -ivh kernel-{version}.{arch}.rpm </code> <br>. This will require a reboot. 
    - **rpm2archive** is use to convert RPM packages files to **tar** archives. 

