---
layout: post
---
- **dnf** caches information and databses to speed up performance. To remove cached information: <br>
<code> dnf clean [ packages | metadata | expire-cache | rpmdb | plugins | all ] </code> <br>
You can also toggle use of a particular repo on or off by changing the value of **enabled**, or using the **--disablerepo {repo}** and ** --enablerepo {repo}** options. <br>
- **dnf** replaced **yum** during the RHEL/CentOS 7 to 8 transition. 
- dnf queries: 
    - To search for a package with a keyword: <br> <code> dnf search {keyword} </code> <br>
    - To display information about a package: <br> <code> dnf info {package} </code> <br>
    - To list packages installed, available, or updates: <br> <code> dnf list [installed | updates | available ] </code> <br>
    - To show information about package groups installed: <br> <code> dnf grouplist </code> <br>
    - To show information about a package groups: <br> <code> dnf groupinfo {package} </code> <br>
    - To show owner of the package for a file: <br> <code> dnf provides {directory} </code> <br>
    - To install: <br> <code> sudo dnf install {package} </code> <br>
    - To install locally: <br> <code> sudo dnf localinstall {package} </code> <br>
    - To install a specific software group from a repository: <br> <code> sudo dnf groupinstall {package} </code> <br>
    - To remove a package: <br> <code> sudo dnf remove {package} </code> <br>
    - To update a package: <br> <code> sudo dnf update {package} </code> <br>
    - List **dnf** plugins: <br> <code> sudo dnf list "dnf-plugin*" </code> <br>
    - List of enabled repos: <br> <code> sudo dnf repolist </code> <br>
    - Interactive shell which to run multiple dnf: <br> <code> sudo dnf shell {file} </code> <br> where file is the list of commands. 
    - Only download the package with the flag **--downloadonly** 
    - Clean up locally stored files and metadata: <br> <code> sudo dnf clean [packages|metadata|expire-cache|rpmdb|plugins|all] </code> <br>

- **zypper**: serves the same function as **dnf** for OpenSUSE. 
- 