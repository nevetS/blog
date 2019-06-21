+++
title = "Configuration file: functions"
author = ["Steve Kallestad"]
lastmod = 2019-05-27T05:20:52-07:00
tags = ["configuration"]
categories = ["orgmode"]
draft = false
weight = 3002
+++

The functions.el file within my org-mode config is simply that.  Function
definitions take up a lot of space, and in my org-mode config, there are a few
that are very verbose.  I've pulled them all into this file in order to make
the remainder more readable.

In here I have a set of functions from [Bert Hansen's org-mode configuration](http://doc.norang.ca/org-mode.html):

| Function             | Purpose                                                                |
|----------------------|------------------------------------------------------------------------|
| bh/hide-other        | collapse all trees but the one you are currently working in (`<f9> h`) |
| bh/make-org-scratch  | create a scratch.org file in /tmp/publish/scratch.org (`<f9> o`)       |
| bh/switch-to-scratch | switch to buffer "**scratch**" (`<f9> s`)                              |

_oh boy, two of those functions don't belong in my org config._

I also have another function `endless/insert-key` which is used to insert a
keybinding into org files.  I have this mapped to `C-c k` so that I can easily
put keybindings into my org files.
