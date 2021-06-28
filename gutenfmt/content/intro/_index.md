+++
title = "Introduction"
+++

*gutenfmt* is a library that helps you to create stand-alone Go applications,
which support different output formats, including, but not limited to YAML, JSON and TSV.
We take an opinionated view of the third-party libraries, so that you can get started with minimum fuss.
In other words, __[Formatters]({{< relref "../lib/#formatter" >}})__ come with meaningful defaults.

We also provide a [command line tool]({{< relref "../cmd/" >}})
that can be used to convert different input formats to various output formats.

__Our primary goals are:__

- Provide a radically faster and widely accessible getting-started experience
  for Command Line Interface (CLI) development.

- Be opinionated out of the box but get out of the way quickly
  as requirements start to [diverge from the defaults]({{< relref "../lib/custom" >}}).

- Provide a range of standardized output formats that are common state-of-the-art projects.

- Absolutely no additional tooling and no requirement for declarative configuration.

# What to read next

Hopefully, this section provided a brief overview of the *gutenfmt* capabilities.

If you are here to use the *gutenfmt* application to convert structured input to other formats,
go to the [Manual]({{< relref "../cmd" >}}) and learn more about its command line options.

If you are a task-oriented type of developer,
you might want to jump over to [Go Library]({{< relref "../lib" >}})
and learn more about the different [concepts]({{< relref "../lib/getting-started" >}})
that solve specific problems.

Otherwise, the next logical step is to take a look at the [Examples]({{< relref "../lib/examples" >}})
and reuse provided code snippets in your application.
