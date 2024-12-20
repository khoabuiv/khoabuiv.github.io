---
layout: default
---

## Terminology

- ansible-navigator: It's like Vim but for ansible
- Ansible playbook: A repeatable, reusable, simple configuration management and multi-machine deployment system
- Ansible inventory: Multiple managed nodes or “hosts” in your infrastructure
- Ansible play: a set of instruction which describe a set of configurations or steps to implement on managed hosts. 
- Ansible playbook: text files written in YAML format to describe a set of plays. 
-- Hosts: the managed hosts to perform the tasks on
-- Tasks: the operations to be performed by invoking Ansible modules and passing them the necessary options.
-- Become: privilege escalation in Playbooks, same as using -b in the ad hoc command.

## Setting up lab environment


### Citation

- [Installing Ansible on WSL](https://phoenixnap.com/kb/install-ansible-on-windows)

### Ansible in the Cloud

For this excercise, I use AWS: 

1. Create an access key in AWS Console
2. 
