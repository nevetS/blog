+++
title = "Organizing your files"
author = ["Steve Kallestad"]
lastmod = 2019-05-27T03:46:49-07:00
tags = ["learn"]
categories = ["orgmode"]
draft = false
weight = 2001
+++

How you organize your files with org-mode is very flexible.  There are a lot of
references around the web for how people organize their own files, and when it
comes down to it, the structure that you fall into is very personal.
Fortunately, re-organizing in org-mode is pretty straightforward.

My configuration specifies that you use the `~/Documents/tasks` directory to
house these files.  You can create files in that path, or you can update the
configuration (in `configs/org/config_variables.el` and
`configs/org/capture-templates.el`)

| Org File   | Description                   |
|------------|-------------------------------|
| todo.org   | Personal tasks                |
| refile.org | Default task capturing bucket |

Why would you capture tasks in one file, and manage them in another?  It won't
be too long before you want to split out your tasks into different files based
on the quantity of tasks within a given category.  Let's start building an
outline for todo.org and you'll be able to understand a little better.

If you only have 10 things to do, it makes sense to just capture them in a
list.  Most of us have a lot more, and keep a running task list in context.

For instance, with your personal TODO's you might put things into four categories

```org-mode
* House
* Finances
* Health
* Family
```

Depending on your lifestyle, any one of these categories could have 10 tasks in
it.  After a month, one of those task lists might become so long (including
current TODOs and history), that it might deserve it's own file.

When you start incorporating your professional task list into org-mode, you
might want a separate file for each project, and maybe an archive file to store
history for quarerly or annual reports.

Start with these two files. Capture your current TODO list.  Learn the refiling
workflow.  Move sections into new files as needed.

Brent Hansen has some [ideas for org file organization](http://doc.norang.ca/org-mode.html#OrgFiles) as you grow.  Sacha Chua
has a blog post on how she [organizes her org files](https://sachachua.com/blog/2013/08/emacs-how-i-organize-my-org-files/).  Charles Cave describes his
set of files for [GTD with org](http://members.optusnet.com.au/~charles57/GTD/gtd%5Fworkflow.html#sec-4).

If you are getting started, create two new files: `todo.org` and `refile.org`.
Use those to get started.  Grow from there.
