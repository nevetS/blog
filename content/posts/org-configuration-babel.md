+++
title = "Configuration files babel"
author = ["Steve Kallestad"]
lastmod = 2019-05-31T09:48:27-07:00
tags = ["configuration"]
categories = ["orgmode"]
draft = false
weight = 3003
+++

Babel enables source blocks in org-mode.  The following languages are supported
by default.  Additional requirements may be necessary to install.  For install
requirements, so the orgmode page on [languages](https://orgmode.org/worg/org-contrib/babel/languages.html).

The following languages are configured:

| Language        |
|-----------------|
| python          |
| shell           |
| R               |
| org             |
| sql             |
| sass            |
| sed             |
| awk             |
| css             |
| calc            |
| gnuplot         |
| dot (graphviz)  |
| java            |
| javascript (js) |
| lisp            |
| makefile        |
| browser         |
| http            |

Having language support in org-mode is very powerful.  It allows you to edit
code blocks in their native environment.  You can execute source blocks, and
you can pass data between source blocks.  You can easily pass data between
languages, and you can leverage source blocks from one org file in another,
creating a library of functions that can be used anywhere.
