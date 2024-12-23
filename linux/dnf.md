---
layout: post
---
- **dnf** caches information and databses to speed up performance. To remove cached information: <br>
<code> dnf clean [ packages | metadata | expire-cache | rpmdb | plugins | all ] </code> <br>
You can also toggle use of a particular repo on or off by changing the value of **enabled**, or using the **--disablerepo {repo}** and ** --enablerepo {repo}** options. <br>
- **dnf** replaced **yum** during the RHEL/CentOS 7 to 8 transition. 
- dnf queries: 
    - To search for a package with a keyword: <code> dnf search {keyword} </code>
    - To display information about a package: <code> dnf info {package} </code>
    - To list packages installed, available, or updates: <code> dnf list [installed | updates | available ] </code>
    - To show information about package groups installed: <code> dnf grouplist </code>
    - To show information about a package groups: <code> dnf groupinfo {package} </code>
    - To show owner of the package for a file: <code> dnf provides {directory} </code>
    - To install: <code> sudo dnf install {package} </code>
    - To install locally: <code> sudo dnf localinstall {package} </code>
    - To install a specific software group from a repository: <code> sudo dnf groupinstall {package} </code>
    - To remove a package: <code> sudo dnf remove {package} </code>
    - To update a package: <code> sudo dnf update {package} </code>
    - List **dnf** plugins: <code> sudo dnf list "dnf-plugin*" </code>
    - List of enabled repos: <code> sudo dnf repolist </code>
    - Interactive shell which to run multiple dnf: <code> sudo dnf shell {file} </code> where file is the list of commands.
    - Only download the package with the flag **--downloadonly**
    - Clean up locally stored files and metadata: <code> sudo dnf clean [packages|metadata|expire-cache|rpmdb|plugins|all] </code>

- **zypper**: serves the same function as **dnf** for OpenSUSE. 
- 