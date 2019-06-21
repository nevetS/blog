+++
title = "R"
author = ["Steve Kallestad"]
lastmod = 2019-06-03T00:09:16-07:00
categories = ["orgmode", "diagrams"]
draft = false
weight = 3007
+++

`R` can be used to generate graphs in org-mode as well.

To display/export images, you need to add `:results output graphics` to your
source block header.

```R
library(ggplot2)

ggplot(mpg, aes(displ, hwy, colour = class)) +
  geom_point()
```

{{< figure src="/ox-hugo/r_mpg.png" >}}
