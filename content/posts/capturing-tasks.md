+++
title = "Capturing Tasks"
author = ["Steve Kallestad"]
lastmod = 2019-05-27T04:46:03-07:00
tags = ["learn"]
categories = ["orgmode"]
draft = false
weight = 2002
+++

## What to do when you have something to do {#what-to-do-when-you-have-something-to-do}

Capturing a task is as simple as using the keychord `C-c c`, selecting a
template, and recording your task.  When done recording, use the keychord `C-c
c` again, and your task is then moved into refile.org where you can address
organization later.

The keychord `C-c c` is available globally within emacs (in my configuration -
this is a customization, spelled out in `configs/org/keybindings.el`).

Capturing tasks is easy.  When getting started with org-mode, deciding on what
tasks to capture is the hard part.  Referencing GTD®, my recommendation is to
capture everything that's on your mind.  If you have to do it, capture it.

Org-mode is flexible.  Some tasks you will want to set a deadline for.  Some
tasks you will want to capture how much time you spent on them.  Some tasks
you'll want to track when it's in progress and when it's done.  With others
you just want to note down something you've completed.  Because everything is
text based, treating tasks differently is pretty simple.

The best way to go about things is to keep it simple.  Start tracking tasks.
Mark them as in progress or complete as you work on them.  Learn more advanced
functionality as you get used to working in the system.  You aren't going to
memorize 30 keybindings today.  You aren't going to memorize workflow.  For
now, just remember `C-c c`.  Remember everything gets tracked in refile.org
(until you refile it).  Work your tasks directly in refile.org for the time
being.  When you've done 10 or 20 tasks, learn how to refile them.


## Selecting a template {#selecting-a-template}

After pressing `C-c c`, you are presented with a list of existing templates.

{{< figure src="/images/select-capture-template.png" >}}

You'll notice that there's a letter inside brackets (`[]`) on the left, and a
capture template name on the right.  Press the letter of the capture template
that you want to use.  In my experience, most tasks are going to follow the
`todo` template, so `C-c c t` is a keychord that I have memorized.  It takes me
effort to slow myself down enough to choose a different template.


## Filling out the template {#filling-out-the-template}

{{< figure src="/images/todo-template.png" >}}

Your cursor starts right after "TODO".  Just start typing a description of the
task right away.  If it's more than a few words, write a descriptive title and
add more detailed text to the bottom.

You'll notice a few other things in this template.  It created a "LOGBOOK" -
inside the logbook is simply a timestamp.  It's for tracking time worked on
tasks.  You can leave it or delete it.

You'll also see a timestamp just below the logbook.  When you export task lists
to html for sharing, the `:LOGBOOK:` and any `:PROPERTIES:` that are defined
are generally not exported.  The timestamp within the task body is helpful for
sharing.

You'll also see a hyperlink to the source of the task.  That can be helpful or
not.  If it won't be helpful, simply delete it.

Any details can be added either right after your task title, or at the bottom
of the buffer.
![](/images/todo-example.png)

When you are done, `C-c C-c` again, and the task is captured to `refile.org`.
