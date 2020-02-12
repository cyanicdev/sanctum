---
layout: post
title: NeverLAN CTF 2020 Write-up
date: 2020-02-08T14:30:10.000+00:00
author: dotjam
categories:
- ctf
- writeups
header_img: https://blog.cyanic.me/assets/img/NeverLAN%202020.jpg

---
## Baby RSA

## Browser Bias

This challenge gives us very little information, just a url to a site that tells us `Sorry, this site is only optimized for browsers that run on commodo 64`. However, this also narrows our focus down to a singular goal - trying to convince the website that we are accessing it from a whatever a 'commodo 64' is.

The first thing we need to know is how the browser can determine what type of client is making a request to it. It turns out, a site can only determine this through the `User-Agent` header. We can manipulate this information in a variety of ways - like with browser extensions or on some browsers using the Developer Tools - but for the sake of controlling exactly what headers are passed over we made this handy little python function.

<script src="[https://gist.github.com/javadhamidi/889226036803bab244ae41b127dc0ab3.js](https://gist.github.com/javadhamidi/889226036803bab244ae41b127dc0ab3.js "https://gist.github.com/javadhamidi/889226036803bab244ae41b127dc0ab3.js")"></script> 

Next we have to figure out what our user-agent string should actually be. If we pass 'commodo 64' as the user-agent parameter of our function nothing changes. Googling commodo 64, we get results for the 