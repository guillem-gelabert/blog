---
title: "Strict Transport Security: HTTPS and HTTPS only"
date: 2020-08-22T08:14:15+02:00
draft: false
---

How many times did we, in the early days of internet, type `http://www`? Thanks to the browser's integrated search and autocomplete this isn't the case anymore, most of us just write `my-bank.com` and expect the browser to do the rest. This can have security implications which Strict Transport Security (HSTS) tries to solve.

The problem is that the browser prepends by default the insecure `http://` scheme even if the website we're trying to visit supports HTTPS. Most probably the website will redirect all traffic to their secure version, but a man-in-the-middle could tamper that redirection to show send you to a malicious page.

The HSTS header tells the browser to remember the protocol and to only connect to the secure version. Note that the first time you visit a website you'll still be vulnerable to this type of attack, as the url is not yet in the browsers HSTS registry, but as long as you've visited that website before, you'll be safe.

To protect that first contact you can use the `preload` flag, instructing the browser to check if your  domain is registered to Google's HTSTS preload service.