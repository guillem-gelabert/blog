---
title: "Referrer-Policy: Whatever I've been doing is non of your business"
date: 2020-08-24T09:19:26+02:00
draft: false
---

The infamously misspelled Referer Header contains the address where the request originated, it is there for analytics, referrals etc. But as URLs can and do encode all sorts of information as Search Params or Path Variables it can open the door to tracking and leaking.  The Referrer-Policy header allows you to limit the content of that header.

You can send the whole URL, send only the origin (scheme/protocol plus domain) or completely obscure the Referer. And you can do it depending on the the security (is it at least equally secure?) and origin of the target (same origin or cross origin):

| Header value                      | Same Origin   | Cross Origin  | Equally Secure | Less Secure
| :-------------------------------- | :-----------: | :-----------: | :------------: | ------------: |
| `no-referrer`                     | nothing       | nothing       | nothing        | nothing       |
| `origin`                          | only origin   | only origin   | only origin    | only origin   |
| `same-origin`                     | only origin   | nothing       | -              | -             |
| `origin-when-cross-origin`        | whole URL     | only origin   | -              | -             |
| `strict-origin`                   | -             | -             | only origin    | nothing       |
| `no-referrer-when-downgrade`      | -             | -             | whole URL      | nothing       |
| `strict-origin-when-cross-origin` | -             | -             | whole URL      | only origin   |
| `unsafe-url`                      | whole URL     | whole URL     | whole URL      | whole URL     |
