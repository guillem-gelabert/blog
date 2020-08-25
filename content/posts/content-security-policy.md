---
title: "Content-Security-Policy: you're not on the guest list"
date: 2020-08-21T16:29:46+02:00
draft: false
categories: ["Security Headers"]
---

Content-Security-Policy works like a guest list for resources, or more like a bouncer with highly specific acceptance criteria. It allows for very granular control on which origins should be allowed and for which cases: specifically for iframes, forms tags, images sources, fonts, XHR or WebSockets connections and plenty more ([there are 14 directives](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy#Directives)).

So you can tell the browser to accept Google Fonts, Bootstrap's CDN, and images from your AWS S3 bucket, and nothing more. Many of the directives inherit from `default-src`, so by setting it you'll be on the safe side.

Another handy feature is the alternative Content-Security-Policy-Report-Only header, which tells the browser not block anything but to report all abuses (sources not complying with your policies) to a given URI (`report-uri`). This makes the most sense as a transition between no CSP header at all and the blocking one and can help you refine your final policies.