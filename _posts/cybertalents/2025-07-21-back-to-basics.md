---
layout: post
title: "Back to Basics"
date: 2025-07-21
categories: [Web]
---

# Web - Back to Basics

## Challenge: Light up the darkness

**Site:** `http://wcamxwl32pue3e6mg1y3e2ptxvm6qyz8l9o8u93w-web.cybertalentslabs.com/`

**Objective:**  
Find the flag and determine what causes it to appear.

## Reconnaissance

```sql
Running Apache 2.4.38 
OS = Debian 
HTML page served via index.html

Key Observations:

    View-source is blocked

    curl works reliably

    Site source reveals interesting restrictions:

html

<!DOCTYPE html>
<html>
    <head>
        <title>Playdead</title>
        <script src="disable.js"></script>
        <!-- ... -->
    </head>
    <body>
        <script>
            document.onkeydown = function(e) {
                if (e.ctrlKey && (e.keyCode === 67 || 86 || 85 || 117)) {
                    alert('No No :)');
                    return false;
                }
            };
        </script>
    </body>
</html>

Exploitation
Step 1: Investigate disable.js
bash

curl http://target-site/disable.js

Step 2: Retrieve Flag

The JavaScript file contains:
javascript

document.addEventListener('contextmenu', function(e) {
    e.preventDefault();
    alert('NO NO NO ;)');
    // FLAG{OkaY_I_FailEd_tO_kEEp_yOu_awAy_hEre_iS_yOur_fLAg} 
});

Solution
Found Flag:
text

FLAG{OkaY_I_FailEd_tO_kEEp_yOu_awAy_hEre_iS_yOur_fLAg}

Vulnerability:

    Client-Side Security Fail:

        Flag stored in client-side JavaScript

        Right-click prevention is easily bypassed

        Security through obscurity is ineffective

Key Takeaways

    Never store sensitive data in client-side code

    Client-side restrictions can always be bypassed

    Proper security requires server-side validation

Tags: #CTF #WebSecurity #ClientSideVulnerabili
