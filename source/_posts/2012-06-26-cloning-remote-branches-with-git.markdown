---
layout: post
title: "Cloning remote branches with Git"
date: 2012-06-26 14:08
comments: true
categories: [git, tips]
---

After cloning locally a remote git project with multiple branches, you will only get the default
project branch, typically `master`. At this point executing `git branch` will show you the locally available
branches in your repository:

```sh
$ git branch
* master
```

However if you add the `-a` option to `git branch` you'll get a list, which also includes all the available
remote brances, like this:

```sh
$ git branch -a
* master
  origin/HEAD
  origin/master
  origin/source
  origin/foobar
```

Using this list as a reference, we can now create a local tracking branch to work on, for example:

```sh
git checkout -b source origin/source
```

The `source` branch will now be checked out and available locally, which we can see by running
`git branch` once again:

```sh
$ git branch
  master
* source
```

That's it! There's also the `git pull --all` command which will fetch all the remote branches
that have been tracked locally, however it **will not** create local tracking branches.
There is no git native way of automatically creating local tacking branches of all remotes and
this is perhaps not a good idea anyway, as they can get stale rather quick.
