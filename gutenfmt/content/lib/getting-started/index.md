+++
title = "Getting Started"
+++

## Concepts

- [Writer]({{< relref "#writer" >}})
- [Formatter]({{< relref "#formatter" >}})
- [Resolver]({{< relref "#resolver" >}})

## Writer

__gfmt.Writer__ is the interface that wraps the generic __Write__ method,
which writes arbitrary types to the underlying output stream.
Typically, this is an __io.Writer__ such as __http.ResponseWriter__.
__Write__ returns the number of bytes written and any __error__ encountered
that caused the write to stop early.

```go
type Writer interface {
	Write(i interface{}) (int, error)
}
```

## Formatter

A __gfmt.Formatter__ converts values of a certain type to their string representation.

```go
type Formatter interface {
	Format(i interface{}) (string, error)
}
```

Typically, __Formatter__ implementations are not used directly.
Instead, they are used by __Writer__ to customize the output of complex data types.
Unlike __Writer__, a __Formatter__ should be stateless and could be used concurrently.

## Resolver

A __Resolver__ returns field metadata for the given __struct__ type.
In particular, a __field__ holds information like

- the actual field name as defined in the __struct__, and
- a custom field name that should be used in the output.

```go
type Resolver func(typ reflect.Type) []field
```

By default, *gutenfmt* uses a __Resolver__, based on __encoding/json__.
It uses reflection to lists fields that JSON should recognize for the given type.
The algorithm is breadth-first search over the set of structs to include -
the top struct and then any reachable anonymous structs.

The default __Resolver__ assumes JSON semantics.

However, this is can be customized as follows: [Use different metadata for a struct]({{< relref "custom#resolver" >}})

## Examples

More comprehensive examples, including, but not limited to

- applying a custom __Formatter__,
- using horizontal and vertical table format, and
- formatting an arbitrary __struct__ or __map__ to YAML

can be found on the [Examples]({{< relref "examples" >}}) page.
