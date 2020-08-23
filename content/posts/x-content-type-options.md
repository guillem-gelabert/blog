---
title: "X-Content-Type-Options: Don't sniff the mimetype"
date: 2020-08-23T13:21:59+02:00
draft: false
---
With [Content-Security-Policy](/posts/content-security-policy/) you can avoid foreign scripts from being executed, but you can still inject malicious code as plaintext and let the browser figure out that it should be handled like code, defeating the whole purpose of CSP.

We've seen that browsers being nice and tolerant, often by making assumptions about the users intentions or the content, had sometimes security implications. One example is the smart address bars that prepends  `http://`  even if a site supports HTTS, which can be mitigated with the [HSTS Header](/posts/strict-transport-security/). Another case of a browser being too smart is when it tries to inferr the content type of a source to handle it accordingly, that is called mimetype sniffing, and can be prevented by including the header `X-Content-Type-Options: nosniff`.