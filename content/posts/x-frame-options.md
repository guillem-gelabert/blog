---
title: "X-Frame-Options: iframes are so 2005"
date: 2020-08-25T08:45:52+02:00
draft: false
---

Back in the day _iframes_ were used everywhere —keeping the URL the same while navigating, embedding Adobe Reader, even as a layouting tool 🤦🏽‍♀️— but they can circumvent some CSP policies, are an accessibility nightmare and most notably they are the main medium of _clickjacking_ attacks. That's why they've ve fallen from grace and because there are better alternative for almost every use case.

> **Clickjacking** works by placing a legitimate website inside of an _iframe_ and overlaying a transparent element with malicious intentions. Users think they are interacting with with the content of the _iframe_ but their are actually clicking somewhere else.

Okay, the [Content-Security-Policy header](/posts/content-security-policy/) can block _iframes_ with its `frame-ancestors` directive, but X-Frame-Options has a [broader support](https://caniuse.com/#feat=x-frame-options).

It accepts the following directives:

- `DENY`: your site cannot be shown in an iframe.
- `SAMEORIGIN`: your site can only be shown in iframes with the same origin.
- `ALLOW-FROM`: allows you to specify an authorized target.

`SAMEORIGIN` and `ALLOW-FROM` are not reliable as they depend on browser implementation, so the best is to use both headers: CSP with `frame-ancestors` and `X-Frame-Options: DENY` to completely disable _iframes_ for legacy browsers.
