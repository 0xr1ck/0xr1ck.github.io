---
layout: default
title: Home
---

# Welcome 
This is where I document my journey through - vulnerability research, exploit development, CTFs, Bug bounty hunting and more
breaking and fixing for fun & profits and if you have any questions or comments you know what to do....!

## Latest Posts

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%B %d, %Y" }}
{% endfor %}

## Focus Areas

- **Binary Exploitation** - Memory corruption, ROP chains, heap exploitation
- **Web Application Security** - OWASP Top 10, API security, client-side attacks  
- **Network Penetration** - Active Directory, lateral movement, privilege escalation
- **Malware Analysis** - Reverse engineering, dynamic analysis, threat hunting
- **Red Team Operations** - C2 frameworks, OPSEC, social engineering

---

*"The best way to secure a system is to think like an attacker."*
