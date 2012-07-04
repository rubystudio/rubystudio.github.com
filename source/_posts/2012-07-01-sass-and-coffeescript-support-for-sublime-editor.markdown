---
layout: post
title: "SASS and CoffeeScript support for Sublime Editor"
date: 2012-07-01 20:02
comments: true
categories: [tips, rails]
---

My current programming editor of choice is [Sublime Editor 2](http://www.sublimetext.com/). Its code
highlighting and snippets component supports a host of languages by default, however SASS and CoffeeScript
are still not in the defaults, even after the [recent update](http://www.sublimetext.com/blog/articles/sublime-text-2-0-released).

Luckily Sublime supports TextMate bundles, so there's an easy way to add the missing bits and pieces.
Here's how to do it step by step:

#### Get the [SASS](https://github.com/n00ge/sublime-text-haml-sass) and [CoffeeScript](https://github.com/jashkenas/coffee-script-tmbundle) bundles (both available on github):

```sh
git clone git://github.com/n00ge/sublime-text-haml-sass.git
git clone git://github.com/jashkenas/coffee-script-tmbundle.git
```

#### Open the Sublime Editor `Packages` folder

{% img right http://i.imgur.com/GGEU9m.jpg %}

This is the folder containing all the syntax highlighting bundles. Its location differs, depending on
the OS you're using, so best way to open it is via the editor's *Preferences > Browse Packages...* menu entry:

#### Copy the new bundles into the `Packages` folder

For SASS you only need the `SASS` directory from the cloned repository. Disregard the `Sass` and `Ruby Haml`
folders. By the time of this writing Subilme already ships with built-in support for Ruby Haml.

For CS you need the entire cloned `coffee-script-tmbundle` repo as a folder, so copy it directly into `Packages`,
optionally renaming it into something shorter and cleaner, like "CoffeeScript".

#### Now restart Sublime Editor to activate your new bundles

That's it. Enjoy working with SASS and CoffeeScript!
