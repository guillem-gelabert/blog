---
title: "X-XSS-Protection: a security header gone wrong"
date: 2020-08-20T21:37:47+02:00
draft: false
categories: ["Security Headers"]
---

In 2010 Chrome shipped a new feature, XSS Auditor, that would prevent unsafe parts of the website to be rendered. Together with XSS Auditor a new HTTP Header was introduced, with which its behaviour could be controlled. It provided the following options:
- `0`: Disabled
- `1`: Prevent unsafe parts from rendering
- `1;mode-block`: Prevent whole page from rendering
- `1;report=<reporting-URI>`: Which blocks rendering and reports the abuse

XSS Auditor worked mainly by checking if any pieces of code were both present in the request and its subsequent response, in a so called _reflection_ attack. This happens, for example, if an attacker is able to send some content that will be server side rendered as is, that is to say unsanitized.

Unfortunately, by 2019 this feature has led to a series of exploits. Some allowed attackers to block legit sources, potentially preventing the execution of security-critical scripts (e.g. validation scripts). Others extracted information by trial and error, and detecting if XSS Auditor was being triggered.

It has now been deprecated in most modern browsers in favour of a Content Sercurity Policy, that's why `X-XSS-Protection` should be set to `0`.