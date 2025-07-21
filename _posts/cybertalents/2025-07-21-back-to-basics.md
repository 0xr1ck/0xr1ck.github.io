---
layout: post
title: "Back to Basics"
date: 2025-07-21
categories: [Web]
---

# Light up the darkness - CTF Writeup

**Site:** `http://wcamxwl32pue3e6mg1y3e2ptxvm6qyz8l9o8u93w-web.cybertalentslabs.com/`  
**Objective:** Find the hidden flag and explain what causes it to appear.

## Reconnaissance

- **Server:** Apache 2.4.38 (Debian)
- **Page Source:** Disabled via JavaScript
- **Key Restrictions:**
  - Right-click disabled (triggers alert)
  - View-source blocked (Ctrl+U disabled)
  - Copy/paste prevention (Ctrl+C/Ctrl+V blocked)

## Analysis

### HTML Structure
```html
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

Key Findings:

    disable.js is loaded (suspicious behavior)

    Event Listeners block:

        Right-click (contextmenu)

        Keyboard shortcuts (Ctrl+C, Ctrl+V, Ctrl+U)

Exploitation
Step 1: Bypass Restrictions
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

Flag
text

FLAG{OkaY_I_FailEd_tO_kEEp_yOu_awAy_hEre_iS_yOur_fLAg}

Vulnerability

    Improper Client-Side Security:
    Hiding sensitive information in client-side JavaScript files is insecure as:

        Users can bypass front-end restrictions

        All client-side resources are publicly accessible

        Obfuscation is not a security measure

Secure Alternatives

    Store flags server-side

    Implement proper authentication

    Use Content Security Policies (CSP)

    Avoid security-through-obscurity
