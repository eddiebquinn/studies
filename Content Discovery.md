Topic: #ComputerScience 
Sources: https://tryhackme.com/room/contentdiscovery

---

There are three main types of content discovery which are listed below

## Manually
### [[Robots.txt]] & sitemap.xml
These both serve simmilar purposes, however from a CySec perspective `robots.txt` can give us a hint at endpoints the sysadmin doesnt want us to find. `sitemap.xml` on the other hand can give point us to areas of the wesbite that are difficult to navigate too, or possibly list some old pages that are officially no longer used.

### Favicon
Sometimes when frameworks are used to build a website the favicon is left as the framework default. OWASP host a databse of common framework icons [here](https://wiki.owasp.org/index.php/OWASP_favicon_database).

For example with [this site](https://static-labs.tryhackme.cloud/sites/favicon/) you can see this favicon: ![Favicon](https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico) If you inspect the page source you can find the image on the site is hosted at `/images/favicon.ico/`. You can run the following command to get its hash, which you can cross refrence against the OWASP database
```
eddie@ghost$ curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum
```
### [[HTTP Headers]]
Headers that are returned can sometimes return useful information like
- The webserver software in use
- The backend programming language

The below code block shows an example of how to view this information using the `curl` command
```
$ user@machine$ curl http://10.10.148.205 -v

*   Trying 10.10.148.205:80...
* TCP_NODELAY set
* Connected to MACHINE_IP (MACHINE_IP) port 80 (#0)
 
> GET / HTTP/1.1
> Host: MACHINE_IP
> User-Agent: curl/7.68.0
> Accept: */*

* Mark bundle as not supporting multiuse

< HTTP/1.1 200 OK
< Server: nginx/1.18.0 (Ubuntu)
< X-Powered-By: PHP/7.4.3
< Date: Mon, 19 Jul 2021 14:39:09 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive`
```
### Framework stack
If you know the framework a website is using you can use the frameworks website to learn more about the underlying software i.e. the default credentials.

## [[OSINT]]
### [[Dorking|Google Hacking/Dorking]]
Dorking allows us to take advantage of googles advanced feature to find previously indexed parts of a website that may be hard to navigate to in other circumstances. The below example would be helpful to find an admin portal
```
inurl:admin
```
### Wappalyzer
[Wappalyzer](https://www.wappalyzer.com) is an online browser extension that helps to identify what tech a website uses i.e. frameworks, [[Content Management Systems|CMS's]], payment processors. The real power is that it can tell you the version it is running, and this can be used to find potential [[Common Vulnerabilities and Exposures|CVE's]]

### Wayback machine
Wayback machine can be used to help uncover old pages that may still be active on the current website

### GitHub
Github is just one of many git repo hosting services that can be used for this purpose, but GitHub is the largest by a significant margin. Using github you may be able to find the git repo for the website you are gathering information on i.e. passwords and api tokens. A tool such as [GitLeaks](https://github.com/gitleaks/gitleaks) can be used to expediate this process.

### [[S3 Buckets]]
Sometimes the accsess permissions for S3 buckets are configured incorrectly. These can be discovered in many ways ranging from looking at GitHub to using automated tools. One automation method is by using the company name followed by common search terms. For example
- `{name}-assets`
- `{name}-www`
- `{name}-public`
- `{name}-private`

## Automated discovery
Automated discovery is the process of using tools to do the things which were discussed in [[#Manually]] and [[#OSINT]]. This process is automated because it can contain thousands to millions of web-requests, and is made possible using [[Wordlists|wordlists]].

The big three tools used on [THM](tryhackme.com) are
- [[ffuf]]
- [[dirb]]
- [[gobuster]]