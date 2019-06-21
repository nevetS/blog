+++
title = "wsd-mode"
author = ["Steve Kallestad"]
lastmod = 2019-06-03T00:08:35-07:00
categories = ["orgmode", "diagrams"]
draft = false
weight = 3002
+++

`wsd-mode` uses [websequencediagrams.com](https://www.websequencediagrams.com/) to generate sequence diagrams.  A set of
[example diagrams](https://www.websequencediagrams.com/examples.html) is available to help you get going with building a diagram.

You can use any of the following styles with your websequencediagram:

-   default
-   earth
-   magazine
-   modern-blue
-   mscgen
-   napkin
-   omegapple
-   patent
-   qsd
-   rose
-   roundgreen

You can also see details about wsd-mode at the [wsd-mode source repository](https://github.com/josteink/wsd-mode).
The default is modern-blue.  Here's a sample showing a simplified SAML
workflow:

First, let's use a little lisp to set the style:

```emacs-lisp
(set 'wsd-style '"napkin" ) ; note you have to quote the quoted value
```

`C-c` to execute and you'll get the following result:

```text
napkin
```

That just means that the variable has been set.

```wsd
title SAML Sequence
participant SP
participant UA
participant IDP

UA->SP: Request Resource
SP->UA: SSO Redirect (w/ XML payload)
UA->IDP: Request SSO
IDP->IDP: Validate User
IDP->UA: (encrypted) XML Response
UA->SP: Request Assertion Service
SP->UA: Redirect to target
UA->SP: Request Target
SP->UA: Respond with Target Resource
```

{{< figure src="/ox-hugo/SAML.png" >}}
