+++
title = "graphviz"
author = ["Steve Kallestad"]
lastmod = 2019-06-03T00:08:50-07:00
categories = ["orgmode", "diagrams"]
draft = false
weight = 3003
+++

Graphviz is probably my favorite diagram tool.  Syntax required to build a
diagram is pretty simple, and layout is determined by graphviz.  It's a little
restrictive and hard to create some kinds of diagrams, but for a lot of simple
diagrams it's very easy to work with.

This is a sourceblock that is named `gv-pretty`.  I can include this by name in
another sourceblock using the `:noweb yes` tag and then including
`<<gv-pretty>>` where it should be included

<a id="code-snippet--gv-pretty"></a>
```dot
rankdir="LR"; # left to right direction
graph [fontname="DejaVuSans"
       labelloc="t" # top label position
 ]

# bgcolor="#2e3e56"

node[shape="box"
     fillcolor="lightyellow"
     style="filled"
     color="#CCCCCC"
     penwidth=1 ];
```

{{< figure src="/ox-hugo/gv-sample.png" >}}

The following source created the above diagram

```org
# +BEGIN_SRC dot :noweb yes :file images/gv-sample.png :exports results
digraph {
 #include styling
 <<gv-pretty>>

 # graph header
 graph[label="sample" fontcolor="#29b89d"]

 # diagram
 see->s2
 s2->easy
 easy->see [style=dashed color=blue]

 # configure s2 node
 s2[label="it's" fontcolor="darkgreen" shape="oval"]
}
# +END_SRC
```
