+++
title = "Configuration files overview"
author = ["Steve Kallestad"]
lastmod = 2019-05-27T19:24:08-07:00
tags = ["configuration"]
categories = ["orgmode"]
draft = false
weight = 3001
+++

My configuration for `org-mode` is reasonably complex.  Reading through a long
lisp file when making changes became cumbersome.  I broke the configuration up
into a series of files in the `config/org/` path.  Each file has it's own
purpose to make tracking down and updating configuration values easier.

| File                 | Description                   |
|----------------------|-------------------------------|
| config\_variables.el | org variable configuration    |
| capture-templates.el | templates to capture tasks    |
| agenda.el            | agenda specific configuration |
| babel.el             | babel specific configuration  |
| tasks.el             | task specific configuration   |
