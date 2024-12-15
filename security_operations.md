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

## Cyber Kill chain and detection

- Always expect detection gaps.
- Cyber Kill chain: Initial recon; initial compromise; establish foothold; escalate privileges; internal recon; move laterally; maintain presence; complete mission. 
- MITRE ATT&CK: A popular framework for understanding the different techniques and tactics that threat actors perform through the kill chain 
- Atomic Red Team library: a collection of red team test cases that are mapped to the MITRE ATT&CK framework.
- Performing atomic testing on Windows:
-- Running attack simulation: 
```
PS C:\Users\Administrator> Invoke-AtomicTest {MITRE Code} -ShowDetails
```
-- -Checkprereq flag to show prerequisite.
-- -TestNumbers to use the specific test.
-- -cleanup to clean up the logs
-- System monitor log is stored in: Event Viewer => Applications and Services => Microsoft => Windows => Sysmon => Operational 
