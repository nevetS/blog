+++
title = "Learning emacs"
author = ["Steve Kallestad"]
lastmod = 2019-05-26T15:04:55-07:00
tags = ["learn"]
categories = ["emacs"]
draft = false
weight = 2003
+++

The hardest part of picking up emacs for me was learning to program in it.
Programming tends to have deadlines, and shifting programming tasks into emacs
means finding and learning all of the features that are important to you while
still working under the same deadline.

Rather than push the same bad experience on others, I think the best way of
getting started is with something very simple - using org-mode for task
management.  Over the years, I've seen a hundred different task management
tools and workflows.  People have made careers out of it.  And yet, every tool
that I've seen is lacking in major ways.

I recommend getting started with personal task management - outside of the
workplace - and moving on from there.  Here's why:

1.  It's a good introduction to the emacs interface.
2.  It's a small time and attention consumer.
3.  Learning can be at a comfortable pace.
4.  Like much of emacs, the initially introduced feature-set is small and easy
    to comprehend, but the real power comes from practice, learning about the
    possibilities, and applying those possibilities to your day-to-day.

The first thing to do is install emacs.  Personally, in my Windows environment
I run emacs in a VirtualBox VM in seamless mode (I use Xubuntu because it works
well with seamless mode).  I do that because little things pop up that are only
problems in Windows.  It may or may not be a problem for you.  It may or may
not be a problem in 2019.  But it has been a problem for me in the past and
that's how I've chosen to deal with it.

In OS/X and on Linux, I use a native version.  I compile my own.  The packaged
binaries are pretty good too, but they don't always have the latest and
greatest features enabled.  The [GNU Emacs page](https://www.gnu.org/software/emacs/) has downloads available.  On
your first run (and until you get around to making changes to your
configuration), you will see a link to the Emacs Tutorial.  It covers
navigation, how to interact with files, how to find help.  It's well written
and has evolved over a long period of time (decades maybe).  Run through the
tutorial a few times to gain a comfort level with the basics and when you are
comfortable, come back to my org-mode configuration and tutorials.

If you want to compile your own emacs, I have instructions for Ubuntu.
