Topic: #ComputerScience 
Source: https://tryhackme.com/room/contentdiscovery

---
- Used in automated [[Content Discovery]] and [[Subdomain Enumeration]]

## Basic syntax
```
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt -u http://MACHINE_IP/FUZZ
```
## Flags
|Flag|Usage|Description|
|----|-------|------------|
|-w|-w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt|Specifies which wordlist to use in attack|
|-H|-H "Host:FUZZ.eddiequinn.xyz"| adds/edits a [[HTTP Headers|HTTP header]]|
|-u|-u eddiequinn.xyz|Specifies a target|
|-fs|-f {size}|Allows you to filter results|
