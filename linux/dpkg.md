---
layout: post
---
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
