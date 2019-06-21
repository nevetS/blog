+++
title = "ditaa"
author = ["Steve Kallestad"]
lastmod = 2019-06-03T00:08:57-07:00
categories = ["orgmode", "diagrams"]
draft = false
weight = 3004
+++

`ditaa` allows you to build diagrams from ascii art.  You have to have ditaa
installed (on ubuntu `sudo apt install ditaa`).  Syntax is on the [ditaa repo
page](http://ditaa.sourceforge.net/#usage).  You'll want to update `org-ditaa-jar-path` appropriately (in
`configs/org/org_config_variables.el`).  Package managers will generally install it into
`/usr/share/ditaa/ditaa.jar`.  You can also use `artist-mode` to draw the
boxes, and once drawn it's handy to use overwrite to type inside the boxes.

```ditaa

+----------+	  +-----------+	    +------------+      +-----------\
| {io}	   |	  |{d}	      |	    | {s} c1AB	 |      |cBLU       |
| process  |----->|document   |<--->| database	 |----=>|regular    |
|	   |	  |	      |	    |		 |      |step       |
+----------+	  +-----------+	    +------------+      +-----------/

```

{{< figure src="/ox-hugo/ditaa-ditaa-boxes.png" >}}
