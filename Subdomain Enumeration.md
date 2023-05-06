Topc: #ComputerScience 
Source: https://tryhackme.com/room/subdomainenumeration

---
Subdomain enumeration is the process of finding valid subdomains for a root-domain. This is done in an effort to expand attack surface and discovery potential attack vectors.

There are three main methods, which are detailed in the subheadings below

## Brute Force
### DNS Bruteforce
This is a method of trying a quantity of diffrent possible subdomains from a pre-defined list of commonly used subdomains. Because this method requires many requests, we will typically automate this with tools like [dnsrecon](https://github.com/darkoperator/dnsrecon)

## [[OSINT]]
### SSL/TLS Certs
- When an SSL/TLS cert is created for a domain by a CA, the CA takes part in [[Certificate transparency logs|CT logs]]
- You can use [[Certificate transparency logs#Databases|these tools]] to query these logs
### [[Dorking]]
You can use google dorking to try and find subdomains using the followig query
```
-site:www.eddiequinn.xyz site:*.eddiequinn.xyz
```
### [[Sublist3r]]
Sublist3r is purpose made for this

## Virtual Host
- Some subdomains aren't hosted in public accessible DNS results, instead they may be held on a private DNS server or in a `/etc/hosts` file
- Because web servers can host multiple websites, the server relies on the host [[HTTP Headers|header]] to know why website the client wants
- Simmilar to [[#DNS Bruteforce]] we can automate this proecess by using a [[Wordlists|wordlist]] of common subdomains combined with [[ffuf]]

```
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.eddiequinn.xyz" -u http://10.10.95.96`
```
It should be noted the above command will always return a valid result, so to filter them out you take the most common size that shows up (lets assume its `2395`) and tack on `-fs 2395` to filter those results out
