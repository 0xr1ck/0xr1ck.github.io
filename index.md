---
layout: default
title: Home
---

# Welcome 
This is where I document my journey through - vulnerability research, exploit development, CTFs, Bug bounty hunting and more
for fun & profits and if you have any questions or comments you know what to do.!

## Latest Posts

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%B %d, %Y" }}
{% endfor %}

## Focus Areas

- **Reverse Engineering** - **Web Application Security** - **Open Source Intelligence [OSINT]** - **Exploit Dev && Malware Analysis**  - **Red Teaming** 

---

*"There is a crack in everything. That's how the light gets in" - L Cohen.*
