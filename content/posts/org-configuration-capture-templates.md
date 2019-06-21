+++
title = "Configuration files capture-templates"
author = ["Steve Kallestad"]
lastmod = 2019-06-03T22:07:29-07:00
categories = ["orgmode", "configuration"]
draft = true
weight = 3004
+++

Capture templates are available when you press C-c.  There are several options
to choose from out of the box with my configuration, or you can build your own.

There are templates for:

-   todo
-   respond
-   note
-   Journal
-   Meeting
-   Phone call
-   Hugo post
-   Habit


## defining templates {#defining-templates}

You can define your own templates, and in an effort to explain the templates
that I have in place, I think it's worth going over the process of how to
define them:

<a id="code-snippet--capture template example"></a>
{{< highlight elisp "linenos=table, linenostart=1" >}}
(setq org-capture-templates
    (quote (
	("t"
	 "todo"
	 entry
	 (file "~/Documents/tasks/refile.org")
	 "* TODO %?
%U
%a
"
	 :clock-in t
	 :clock-resume t)
;; ... (other entries)
	    ))
{{< /highlight >}}

Capture templates are stored in a list variable called
`org-capture-templates`.  Each template is comprised of:

-   **keys** `line 3, "t"`: The key or keys that will select the template.
-   description `line 4, "todo"`: a short description describing the template, this does not map
    to any part of the template.
-   **type** `line 5, entry`: The type of entry.  All of the templates I use are "entry" types The
    valid types are:
    -   **entry**: an org node with a headline
    -   **item**: a plain list item
    -   **checkitem**: a checkbox item
    -   **table-line**: a new line in the first table at the target location
    -   **plain**: text to be inserted as is
-   **target** `line 6, file reference`: The file this capture will be placed in.  I use a common file to
    capture items, and refile them later in a proper location.  `C-h v
      org-capture-templates` for other options
-   **template** `line 7-8`: the remaining lines are the template.

Starting on line 7 is the template itself.  Templates can be strings, file
references, or functions that return a template as a string.  In this case we
have a string. To start with we have "\* TODO ".  This section creates a
top-level org item (`*`) and sets the state of that item as "TODO".  Next we
have "%?\n%U\n%a\n".  `\n` is a line return, so it's really:

```shell
%?
%U
%a
```

Expansion for these keywords is spelled out in [The orgmode manual](https://orgmode.org/manual/Template-expansion.html).  `%?` is
where we want the cursor to end up so that you can start typing.  `%U` inserts
the date and time the entry was captured.  `%a` creates a link to the document
that you were in when you captured the entry.

Line 8 is still part of the capture template.  It defines behaviors for this
template.  `:clock-in t` clocks you into this task automatically as you are
creating the template.  It also clocks you out of the task you were working
on.  When the task has been captured or cancelled, `clock-resume t` clocks you
back into what you were working on previously.


## Todo template {#todo-template}

The todo template is my default capture template for anything that will take
more than a minute or two to accomplish.

The 'todo' template is as follows:

```text
* TODO
  :LOGBOOK:
  CLOCK: capture start date/time--capture end time =>  capture duration
  :END:
date/time of capture
link to source file or email
```


## response template {#response-template}

The response template is a note to respond to email.  This is specifically for
emails that are being read within emacs.  You are not prompted for any
information.  The link to the original email will be created, and the entry is
added to refile.org

```text
* NEXT Respond to %:from on %:subject
SCHEDULED: capture date
capture date/timestamp
link to source

```


## note template {#note-template}

The note template is for capturing a note (or set of notes) that are not tasks.
It comes with a NOTE tag so notes can be easily found.

```text
*                  :NOTE:
capture date/timestamp
link to source
```


## Journal template {#journal-template}

The journal template designed to put entries in diary.org.  That file is
organized by date tree.

```text
*
capture date/timestamp
```


## Meeting template {#meeting-template}


## Phone call template {#phone-call-template}


## Habit template {#habit-template}
