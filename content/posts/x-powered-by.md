---
title: "X-Powered-By: the price of vanity (22 bytes)"
date: 2020-08-28T09:47:03+02:00
draft: false
categories: ["Security Headers"]
---

Some web frameworks, most notably Express.js, automatically add the X-Powered-By header. The goal is probably marketing —although we could call it recognition to the team that developed an a free and open source solution. If the framework provides a built-in way to disable it you should do it, otherwise you can overwrite it manually.

There are two —very banal— problems with it:

One, it gives technical information to an attacker, which could be used to try known exploits on that technology against your server. This is poses a [very mild risk](https://github.com/expressjs/express/pull/2813#issuecomment-159270428) as there are other ways to find that out and an automated attack could try exploits for different backend technologies.

And two —and most important—, it is a useless header. We strive to make responses small: compression, minification, bundling, code splitting... Do we want to add even one useless bit to the metadata that comes with it?

That said, one could argue that public recognition of the creators of your framework of choice is worth the 22 bytes. Fair enough.
