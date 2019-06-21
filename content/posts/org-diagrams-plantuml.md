+++
title = "plantuml"
author = ["Steve Kallestad"]
lastmod = 2019-06-03T00:07:41-07:00
categories = ["orgmode", "diagrams"]
draft = false
weight = 3001
+++

One resource to revisit when you see sloppy PlantUML diagrams is this [StackOverflow question](https://stackoverflow.com/questions/48712801/how-to-correct-plantuml-line-path/48735216#48735216).


## ERD Diagrams {#erd-diagrams}

`plantuml` is a bit much to get going.  You need to install java, you need
to [download the plantuml.jar](http://plantuml.com/download) file, and you need to set the
`org-plantuml-jar-path` variable.

ERD diagrams are doable in plantuml, but you cannot (that I know of) link
fields to one another.  It might be good to generate an ERD with a full field
listing for an overall view, and then another diagram that spells out field linkages.

First, we set the path to plantuml.jar

```emacs-lisp
(setq org-plantuml-jar-path '"~/windows/plantuml/plantuml.jar")
```

Then we define our diagram

```plantuml
skinparam monochrome true
skinparam shadowing false

hide circle
hide empty members

title All Fields
entity email {
   * pkid
   * email2user
   * email
}
entity user {
   * pkid
   --
   * username
   first
   last
}
entity phone {
   * pkid
   * phone2user
   * phone
}

email}-||user
user||-{phone
```

{{< figure src="/ox-hugo/class_diagram.png" >}}

Now we define our linkage:

```plantuml
skinparam monochrome true
skinparam shadowing false

hide circle


title Foreign keys
entity user {
  * pkid

}
entity email {
  * email2user

}
entity phone {
  * phone2user

}
email}-||user
user||-{phone
```

{{< figure src="/ox-hugo/crows-feet.png" >}}

Even with only one field, the crows feet don't line up perfectly, but at least
you get to see the relationships.


## Sequence Diagrams {#sequence-diagrams}

You can also do sequence diagrams

```plantuml
skinparam monochrome true
 Foo -> Bar: synchronous call
 Foo ->> Bar: asynchronous call
```

{{< figure src="/ox-hugo/sequence_diagram.png" >}}


## Use case diagrams {#use-case-diagrams}

And use case diagrams:

```plantuml
left to right direction
skinparam monochrome true
skinparam shadowing false
skinparam packageStyle rect
actor customer
actor clerk
rectangle checkout {
  customer -- (checkout)
  (checkout) .> (payment) : include
  (help) .> (checkout) : extends
  (checkout) -- clerk
}

```

{{< figure src="/ox-hugo/usecase_diagram.png" >}}


## class diagrams {#class-diagrams}

You can build  class diagrams:

```plantuml
skinparam monochrome true
skinparam shadowing false

interface Command {
    execute()
    undo()
}
class Invoker{
    setCommand()
}
class Client
class Receiver{
    action()
}
class ConcreteCommand{
    execute()
    undo()
}

Command <|-down- ConcreteCommand
Client -right-> Receiver
Client --> ConcreteCommand
Invoker o-right-> Command
Receiver <-left- ConcreteCommand
```

{{< figure src="/ox-hugo/diagram_class.png" >}}


## and more {#and-more}

There are many diagrams you can create with plantuml.  You can see examples and
example source code and [real-world-plantuml.com](https://real-world-plantuml.com/).
