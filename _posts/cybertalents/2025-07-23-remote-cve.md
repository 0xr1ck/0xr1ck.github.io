---
layout: post
title: "remote CVE - CyberTalents (web)"
date: 2025-07-23
categories: [Web]
---

# remote CVE - CyberTalents (web)

Brief `what's CVE ID could be used against the web application in the below target NOTE: it's an unauthenticated RCE vulnerability`

site = http://wcamxwl32pue3e6me435wj7t8z5xqyz8l9o8u93w-web.cybertalentslabs.com/

### goals 
- find the CVE and ID (number) 
- dig the causes of the vulnerability 
## recon 

- we know that it's drupal cms but what verion ??
- run ``curl -I HEAD http://wcamxwl32pue3e6me435wj7t8z5xqyz8l9o8u93w-web.cybertalentslabs.com/`` using the ``HEAD`` tag(option)  
- 
```sql 
curl: (6) Could not resolve host: HEAD
HTTP/1.1 200 OK
Server: nginx/1.25.2
Date: Wed, 24 Jul 2024 23:58:59 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
X-Powered-By: PHP/7.0.28
Expires: Sun, 19 Nov 1978 05:00:00 GMT
Cache-Control: no-cache, must-revalidate
X-Content-Type-Options: nosniff
Content-Language: en
X-Frame-Options: SAMEORIGIN
X-Generator: Drupal 7 (http://drupal.org)

drupal 7
``` 

- cool we have the sites cms and version 
- lets run ``gobuster`` to look for interesting directories 
- after running it we found ``robots.txt``   
- check the ``CHANGELOG.txt`` directory file in the ``robot.txt``
- googled ``drupal 7.* unauthenticate vulnerabilty``
- found this site `https://www.nsa.gov/portals/75/documents/what-we-do/cybersecurity/professional-resources/csa-drupal-remote-code-execution-vulnerability-cve.pdf` 
- which gives us  the flag = ``CVE-2018-7600 `` 
 
