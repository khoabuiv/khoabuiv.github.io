---
title: Home
layout: default
---

## Linux Distributions:
- Debian: upstream for Ubuntu, Linux Mint, and others. Purely open source focus on stability. 
- Red Hat: CentOS Stream is very close to Red Hat Enterprise Linux. 
- OpenSUSE

## How to Setup sudo:
1. Use <code> su </code> to switch to root
2. Go to <code> /etc/sudoers.d </code>, edit the file, and add the line <code> {username} ALL=(ALL) ALL </code>. The 