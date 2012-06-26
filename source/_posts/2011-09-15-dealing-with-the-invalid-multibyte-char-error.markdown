---
layout: post
title: "Dealing with the “invalid multibyte char” error"
date: 2011-09-15 18:51
comments: true
categories: [ruby, rails, tips]
---

If you happen to use non-ASCII characters in a ruby file within your rails app, say a controller,
library, database seeds, etc, you might have the invalid multibyte char (US-ASCII) error thrown
at you by ruby 1.9.x. This is something you’re bound to experience if you’re developing an app
that is localized in a language that utilizes non-ASCII characters and you’re not using the i18n
libraries of rails to define your strings. The solution is very easy and feels almost magical:

```
# encoding: utf-8
```

Put this line of code on top of all scripts that raise the error. Unfortunately there seems to be
no way to deal with it on application level with a single entry. It's Ruby legacy, but perhaps it
should be considered as a Rails default for future versions.
