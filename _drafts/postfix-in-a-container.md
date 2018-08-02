---
layout: post
title: Postfix in a container.
---

Postfix is a service which forks itself and runs in the background. Postfix
version 3.3.0 added
[container support](http://www.postfix.org/announcements/postfix-3.3.0.html).
As I could not find any official Docker image for postfix, I decided to build
one myself.
