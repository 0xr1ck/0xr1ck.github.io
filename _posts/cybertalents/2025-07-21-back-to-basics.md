---
layout: post
title: "Back to Basics"
date: 2025-07-21
categories: [Web]
---

brief `Light up the darkness` 

site = http://wcamxwl32pue3e6mg1y3e2ptxvm6qyz8l9o8u93w-web.cybertalentslabs.com/

- objective to find the flag 
- and what causes that 
## Recon 

```js
running apache 2.4.38 
os = debian 
html page due to index.html 

```

- site doesn't allow view-source 
- curl works all the time 
- checked site source 

```js
<!DOCTYPE html>

<html>
    <head>
        <title>Playdead</title>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
        <style>
            html {
                box-sizing: border-box;
                overflow-y: scroll;
            }
            body {
                font-weight: 400;
                font-size: 14px;
                color: #515352;
                background-color: #000 !important;
                font-family: Oswald,sans-serif;
                margin: 0;
                padding: 0;
                border: 0;
                font-size: 100%;
                font-weight: 400;
                vertical-align: baseline;
                background: 0 0;
                position: relative;
            }
             .fixed-bg {
                
                z-index: 1000;
                position: fixed;
                box-sizing: inherit;
                left: calc(50vw - 370px);
            }
            .fixed-bg #bgvid {
                width: 1200px;
                width: 100%;
                background: url(img/inside/bg/bg_still.png) no-repeat;
                background-size: auto;
                background-size: cover;
            }
        </style>
        <script src="disable.js"></script>
    </head>

    <body>
        <script>
            document.onkeydown = function(e) {
                if (e.ctrlKey && 
                    (e.keyCode === 67 || 
                    e.keyCode === 86 || 
                    e.keyCode === 85 || 
                    e.keyCode === 117)) {
                        alert('No No :) ');
                    return false;
                } else {
                    return true;
                }
            };
        </script>
        <div class="container">
            <h2>Light the Darkness</h2>
        <div class="main-body">
            <div class="fixed-bg">
            <video autoplay="" loop="" poster="https://playdead.com/css/img/limbo/LIMBO.jpg" id="bgvid">
                <source src="https://playdead.com/css/img/limbo/LIMBO.jpg" type="image/jpeg">
                <source src="https://playdead.com/css/img/limbo/limbo_bg.webm" type="video/webm">
                <source src="https://playdead.com/css/img/limbo/limbo_bg.mp4" type="video/mp4">
            </video>
        </div>

        </div>
        
    </body>
</html>
```

- ```disable.js``` looks intresting 
- curl ```site.com/disable.js```
- gives us the flag 
```FLAG{OkaY_I_FailEd_tO_kEEp_yOu_awAy_hEre_iS_yOur_fLAg} ```

- what cause it

```js
document.addEventListener('contextmenu', function(e) {
    e.preventDefault();
    alert('NO NO NO ;)');
});
```
- clicking the page pops up 'no no no' 

Vulnerability:

    Client-Side Security Fail:

        Flag stored in client-side JavaScript

        Right-click prevention is easily bypassed

        Security through obscurity is ineffective

Key Takeaways

    Never store sensitive data in client-side code

    Client-side restrictions can always be bypassed

    Proper security requires server-side validation

Tags: #CTF #WebSecurity #ClientSideVulnerability

