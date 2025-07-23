layout: post
title: "Hack me if you can - CyberTalents (web)"
date: 2025-07-23
categories: [Web]

# web - hack me if you can

brief `find the rce to get access to the system`

- goal to find rce 
- know how the exploit work 
- exploit the vulnerability 
- get flag 

site = `http://wcamxwl32pue3e6mw93xjqgt7zr8qyz8l9o8u93w-web.cybertalentslabs.com/`
## recon 
- comapny name wines co 
- site running on nginx v 1.25.2 
-  fs libs = fancybox 3.5.6 , bootstrap 4.1.3 cololib 

#### Directory enumeration

```sql 
# dirs

main.js
robots.txt 
```

found the most interesting directories ``main`` and ``robots.txt``
		
```sql
# under robots.txt 
User-agent: Applebot
Disallow: /ajax/
Disallow: /album.php
Disallow: /checkpoint/
Disallow: /contact_importer/
Disallow: /etc/flag_48cbe4247cc8f7937ff091f257b4e160.txt
Disallow: /fbml/ajax/dialog/
Disallow: /feeds/
Disallow: /file_download.php
```

and the flag is ``flag_48cbe4247cc8f7937ff091f257b4e160.txt``

