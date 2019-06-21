+++
title = "Configuration files config_variables"
author = ["Steve Kallestad"]
lastmod = 2019-05-30T02:19:02-07:00
tags = ["configuration"]
categories = ["orgmode"]
draft = false
weight = 3002
+++

The lisp file `config_variables.el` contains a set of org-related configuration
variables.  If there is some minor setup that goes along with setting the
variable, that is allowed as well.

| Variable                  | Setting                            | Purpose                                                           |
|---------------------------|------------------------------------|-------------------------------------------------------------------|
| PATH                      | /Library/TeX/texbin:               | appends the latex binary to the path                              |
| org-agenda-files          | ~/Documents/tasks/                 | The location of org files that are used to build an agenda        |
| org-agenda-log-mode-items | "closed state"                     | Show closed tasks in agenda view                                  |
| org-refile-targets        | org-agenda-files . (:maxlevel . 3) | Use the same files as org-agenda-files as refile targets          |
| org-directory             | ~/Documents/tasks/                 |                                                                   |
| org-default-notes-file    | ~/Documents/tasks/refile.org       | default capture location for tasks                                |
| org-highest-priority      | ?A                                 | Org-mode priorities A-E, default of C                             |
| org-lowest-priority       | ?E                                 |                                                                   |
| org-default-priority      | ?C                                 |                                                                   |
| org-use-speed-commands    | t                                  | use org speed commands                                            |
| org-return-follows-link   | t                                  | pressing enter or clicking on a link within an org file opens it. |
| auto-mode-alist           | ".org,.org\_archive,.txt"          | use org-mode with .org, .org\_archive, and .txt files             |
| org-log-into-drawer       | t                                  | timestamps for state changes are recorded into a drawer           |
| org-use-speed-commands    | t                                  | enable hotkeys when placed at the beginning of a task headline    |

The variable last mentioned is powerful.  Place your cursor at the beginning of
a task headline, and you have a great many options to choose from:

```org
User-defined Speed commands
===========================

Built-in Speed commands
=======================

Outline Navigation
------------------
n   (org-speed-move-safe (quote org-next-visible-heading))
p   (org-speed-move-safe (quote org-previous-visible-heading))
f   (org-speed-move-safe (quote org-forward-heading-same-level))
b   (org-speed-move-safe (quote org-backward-heading-same-level))
F   org-next-block
B   org-previous-block
u   (org-speed-move-safe (quote outline-up-heading))
j   org-goto
g   (org-refile t)

Outline Visibility
------------------
c   org-cycle
C   org-shifttab
    org-display-outline-path
s   org-narrow-to-subtree
=   org-columns

Outline Structure Editing
-------------------------
U   org-metaup
D   org-metadown
r   org-metaright
l   org-metaleft
R   org-shiftmetaright
L   org-shiftmetaleft
i   (progn (forward-char 1) (call-interactively (quote org-insert-heading-respect-content)))
^   org-sort
w   org-refile
a   org-archive-subtree-default-with-confirmation
@   org-mark-subtree
#   org-toggle-comment

Clock Commands
--------------
I   org-clock-in
O   org-clock-out

Meta Data Editing
-----------------
t   org-todo
,   (org-priority)
0   (org-priority 32)
1   (org-priority 65)
2   (org-priority 66)
3   (org-priority 67)
:   org-set-tags-command
e   org-set-effort
E   org-inc-effort
W   (lambda (m) (interactive "sMinutes before warning: ") (org-entry-put (point) "APPT_WARNTIME" m))

Agenda Views etc
----------------
v   org-agenda
/   org-sparse-tree

Misc
----
o   org-open-at-point
?   org-speed-command-help
<   (org-agenda-set-restriction-lock (quote subtree))
>   (org-agenda-remove-restriction-lock)
```
