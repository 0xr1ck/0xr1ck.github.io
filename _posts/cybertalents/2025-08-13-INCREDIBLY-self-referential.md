---
layout: post
title: "INCREDIBLY self-referential  - EcowasCTF - 2023 quals (web)"
date: 2025-08-13
categories: [Web]
---

## INCREDIBLY self-referential 

```
decription : Discover my newest EC2 web service – it features an impressively self-referential element!
```
<p align="center">
<img src="https://raw.githubusercontent.com/0xr1ck/0xr1ck.github.io/main/_posts/cybertalents/img/incredible-1.jpg" alt="ST"/>
</p>

lets get to it, EC2-instance??  vists the site 

<p align="center">
<img src="https://raw.githubusercontent.com/0xr1ck/github.com/0xr1ck/blob/main/_posts/cybertalents/img/site.jpg" alt="ST"/>
</p>

 it does  just as it says image metadata viewer web one! uploaded a jpg and fired up burp to check the response turns out it base64 encode the image 

 
<p align="center">
<img src="https://raw.githubusercontent.com/0xr1ck/0xr1ck.github.io/blob/main/_posts/cybertalents/img/burp%201.jpg" alt="ST"/>
</p>


and yeah you guessed reverse shell but that didn't work so decided to make a quick search about EC2-metadata found this blog https://hackingthe.cloud/aws/exploitation/ec2-metadata-ssrf/ and brought everything back on sight its SSRF all this time,  submitted this http://169.254.169.254/latest/meta-data in the url passed it to repeater, check the response and yeah 

<p align="center">
<img src="https://raw.githubusercontent.com/0xr1ck/0xr1ck.github.io/blob/main/_posts/cybertalents/img/first%20bse.jpg" alt="ST"/>
</p>

base64 decoded it in burp suite decode ```aW5mbwpzZWN1cml0eS1jcmVkZW50aWFscy```  give out this ```info, security-credentialcy``` done then submit this to the ```http://169.254.169.254/latest/meta-data/iam/security-credentials/super-secret-admin-role```  url check response and yeah base64 decode it gives us the flag  

<p align="center">
<img src="https://raw.githubusercontent.com/0xr1ck/0xr1ck.github.io/blob/main/_posts/cybertalents/img/final%20flag.jpg" alt="ST"/>
</p>

```
flag{thats_the_most_effective_tactic_available}
```
