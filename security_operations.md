---
title: Home
layout: default
---

## Log Analysis & ELK

- Use ELK stack to make analyizing logs more bearable
- Blue operation: investigation of the attack itself using tools which enable is to analyse the logs.  
- Red operation: re-creating attacks to see how it was carried out

## Beware what you let the users put in
- Remote Code Execution(RCE): Uploading a script that the server runs gives the attacker control over it.
- Cross-site scripting attack(XSS): Uploading an HTML file that contains an XSS code which will steal a cookie and send it back to the attacker's server.
- system() PHP function: input field is then run against the underlying operating system, and the output is displayed to the user