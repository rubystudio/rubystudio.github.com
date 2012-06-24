---
layout: post
title: "Auto-resizing page elements with jquery mobile"
date: 2011-09-26 18:44
comments: true
categories: [javascript, JQuery]
---

{% img left http://i.imgur.com/CMKxnm.png %}

If you’ve been using jQuery Mobile from the start or if you’re just beginning to play with it
(beta 3 is current at the time of this writing) you might have noticed that in recent versions
auto-resizing of page elements does not work for all devices out of the box and this was not the
case in earlier versions. The answer is simple, but not well documented (if at all):
you need to add the viewport meta tag in your layout:

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```
