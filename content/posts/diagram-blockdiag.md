+++
title = "blockdiag"
author = ["Steve Kallestad"]
lastmod = 2019-06-04T01:30:55-07:00
categories = ["orgmode", "diagrams"]
draft = false
weight = 3005
+++

`blockdiag` is a python based tool for generating block diagams.  Syntax and
some examples can be found in the [blockdiag documentation](http://blockdiag.com/en/blockdiag/index.html).  `blockdiag` also
has a couple of other tools `seqdiag` for sequence diagrams, `actdiag` for
activity diagrams, and `nwdiag` for network diagrams.  Links to the
documentation for those tools can be found on the [blockdiag home page](http://blockdiag.com/en/index.html).

```blockdiag
blockdiag {
  default_fontsize = 13;
  shadow_style = none;
  // Set stacked to nodes, see roundedbox
  stacked [stacked]
  // standard node shapes
  box [shape = box];
  square [shape = square];
  roundedbox [shape = roundedbox, stacked];
  dots [shape = dots];

  circle [shape = circle];
  ellipse [shape = ellipse];
  diamond [shape = diamond];
  minidiamond [shape = minidiamond];

  note [shape = note];
  mail [shape = mail];
  cloud [shape = cloud];
  actor [shape = actor];

  beginpoint [shape = beginpoint];
  endpoint [shape = endpoint];

  box -> square -> roundedbox -> dots;
  // group nodes
  group {
    circle;
    ellipse;
    diamond;
    minidiamond;
    // Set group-label
    label = "example grouping";
    // Set background color
    color = "#77FF77"
    // give the group a border
    //shape = line;
  }
  circle -> ellipse -> diamond -> minidiamond;
  note -> mail -> cloud -> actor;
  beginpoint -> endpoint;

  // node shapes for flowcharts
  condition [shape = flowchart.condition];
  database [shape = flowchart.database];
  terminator [shape = flowchart.terminator];
  input [shape = flowchart.input];

  loopin [shape = flowchart.loopin];
  loopout [shape = flowchart.loopout];

  condition -> database -> terminator -> input;
  loopin -> loopout;
}
```

{{< figure src="/ox-hugo/blockdiag-sample.png" >}}
