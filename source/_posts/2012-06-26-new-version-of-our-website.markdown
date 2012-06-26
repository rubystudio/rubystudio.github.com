---
layout: post
title: "New version of our website"
date: 2012-06-26 16:41
comments: true
categories: [Ruby Studio]
---

We have released the new iteration of our website [rubystudio.net](http://rubystudio.net/). It's a
complete rewrite, featuring a cleaner, more simplified look, taking full advantage of
[Twitter Bootstrap](http://twitter.github.com/bootstrap/) and other JQuery goodies.
Under the hood there are a lot of changes too, most importantly all requests to all rubystudio subdomains
are now handled by a single monolithic app, utilizing the Rails 3.1+ [subdomain APIs](http://railscasts.com/episodes/123-subdomains-revised).
We have also switched our background workers from `delayed_job` to using `redis server` and [resque](https://github.com/defunkt/resque/).

Here are a few screenshot from this version:

<iframe class="imgur-album" width="100%" height="550" frameborder="0" src="http://imgur.com/a/jJCRK/embed"></iframe>
