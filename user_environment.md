---
layout: default
---

### General Notes: 
- Can be list with: **env**, **set**, or **printev**. 
- Important environment variables: 
    - **HOME**: User's home directory.
    - **PATH**: Ordered list of directories to search for porgrams to run. 
    - **PS1**: Command line prompt.
    - **SHELL**: User's default shell.
    - **EDITOR**: User's default editor. 

### How to set environment variables:
- Run <code> VARIABLE=value </code>
- To add a new variable permanently. Edit <code> ~/.bashrc </code> to include **VARIABLE=value** and then start a new shell. 


### How to export environment variables:
- By default, variables created within a script are only available to the current shell. Sub-shells do not have access by default.
- To export a variable: <code> export VAR=value </code> or <code>VAR=value; export VAR </code>
- To modify a variable <br>

The child process is allowed to modify exported variables, but the change in this case will not propagate back to the parent shell.

### History command:
- Show the previous commands.
- Locates at **~/.bash_history**
- Maximum number of lines in the history file stored at the variable **HISTFILESIZE**
- Maximum number of lines of history list in the current session: **HISTSIZE**
- Use **CTRL+R** or history and grep to search history commands.
- Use **!** to start a history substitution 
- Use **!n** to refer to the n-th command line 
- Use **!string** to refer to the most recent command starting starting with the string. 

### Alias: 
- Aliases permit custom definitions. 
- **alias** command show all current alias
- To assign an alias: <code> alias name=command </code>
- Make an alias persistent in **~/.bashrc**
- **unalias** to get rid of one. 