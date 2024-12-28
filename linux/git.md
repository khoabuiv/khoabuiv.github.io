---
layout: post
---


- **Revision Control System**: software used to track changes by storing versions of the file at a point in time capturing with the following:
    - When: timestamp of the capture 
    - What: version
    - Who: user associated with the change
    - Why: extra information about the change. 
- Git is a peer to peer by nature, repository's authority is based on human factors and not technical ones.
- Git basic commands(**git help tutorial**):
    - Starting: 
        - **git clone**: Clone a repo into a new directory
        - **git init**: Create an empty repo or reinitialize an existing one.
    - Working(**git help everyday**):
        - **git add**: Add file contents onto the index.
        - **git mv**: Move or rename a file, directory, or symlink
        - **git restore**: Restore working tree files
        - **git rm**: Remove files from working tree and from the index
        - **git sparse-checkout**: Initialize and modify the sparse-checkout 
    - History and state(**git help revisions**):
        - **git bisect**: Use binary search to find the commit that introduced a bug
        - **git diff**: Show changes between commits, commit and a working tree, etc.
        - **git grep**: Print lines matching a pattern.
        - **git log**: Show commit logs.
        - **git show**: Show various types of objects.
        - **git status**: Show the working tree status.    
    - Tweaking common history:
        - **git branch**: List, create, or delete branches.
        - **git commit**: Record changes to the repo.
        - **git merge**: Join two or more development histories. 
        - **git rebase**: Reapply commits on top of another base tip
        - **git reset**: Read current HEAD to the specified state.
        - **git switch**: Switch branches.
        - **git tag**: Add a tag signed with GPG.
    - Collaborate: 
        - **git fetch**: Download objects and refs from another repo.
        - **git pull**: Fetch from and integrate with another repo.
        - **git push**: Update remote refs. 
- **Global configuration**: Git wants you to setup an author name and email address rather than just the default userId. Setup example: <br>
```
config --global user.name "User Name"
config --global user.email "uname@example.com"
config --global init.defaultBranch main
```
Settings get written to **./gitconfig** file