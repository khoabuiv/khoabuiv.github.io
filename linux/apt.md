---
layout: post
---
## APT(Advanced Packaging Tool)
- Installing **apt-cache** and **apt-file**: <br>
    <code> sudo apt-get install apt-file </code> <br>
    <code> sudo apt-file update </code> <br>
- Search a repository for a package: <br>
    <code> apt-cache search {package} </code> <br>
- Display information for a package: <br>
    <code> apt-cache show {package} </code> <br>
- Display detailed information for a package: <br>
    <code> apt-cache showpkg {package} </code> <br>
- Show all dependencies for a package: <br>
    <code> apt-cache depends {package} </code> <br>
- Search the repo for a file: <br>
    <code> apt-file search {filename} </code> <br>
- List all files for a package: <br>
    <code> apt-file list {package} </code> <br>
- Install a package: <br>
    <code> sudo apt install {package} </code> <br>
- Remove a package: <br>
    <code> sudo apt remove {package} </code> <br>
- Remove a package and its config files: <br>
    <code> sudo apt --purge remove {package} </code> <br>
- Synchronize the package index files with their sources: <br>
    <code> sudo apt update </code> <br>
- Upgrade all available updates to packages already installed: <br>
    <code> sudo apt upgrade </code> <br>
**Note**: Must always run update before upgrade. <br>
- To clean up: <br>
    - <code> apt clean </code> to clean out cache files and and any archived package files. 
    - <code> apt autoremove </code> to gets rid of any packages not needed. 

