+++
title = "Customization"
toc = true
+++

## Formatting maps {#maps}

The order is not specified and is not guaranteed to be the same from one invocation to the next.
If a certain order is required, you must define a custom __Formatter__ and specify the order:

```go
m := map[string]interface{}{"a": "A", "b": "B", "c": "C"}
w := NewTab(os.Stdout)

// Create a custom formatter, which outputs certain map entries in the given order.
ks := []reflect.Value{reflect.ValueOf("c"), reflect.ValueOf("a")}
f := formatter.FromMapKeys("\t", "\t\n", ks...)
// Register the formatter for type map[string]interface{}.
w.Formatter.SetFormatter(reflect.TypeOf(m).String(), f)

n, err := w.Write(m)
// Output:
// c	C
// a	A
```

Similarly, a custom __Formatter__ can be used for __map__ slice:

```go
ms := []map[string]interface{}{m}

// Create another formatter - using FromMapSliceKeys().
// The keys could be the same as before, or different if another output format is needed.
f := formatter.FromMapSliceKeys("\t", "\t\n", ks...)
w.Formatter.SetFormatter(reflect.TypeOf(ms).String(), f)

n, err := w.Write(ms)
// Output:
// c	a
// C	A
```

## Use different metadata for a struct {#resolver}

By default, a reflection-based __Resolver__ extracts field information of __struct__ types.
It looks for the __json__ tag and returns its name, if present, or the field name instead.
The community welcomed tags and has built ORMs, further encodings, flag parsers and much more
around them since, especially for these tasks, single-sourcing is beneficial for data structures.

The default __Resolver__ can be changed so that it looks for another tag such as __yaml__ instead.
This can be done by setting a new __Resolver__.

```go
meta.Resolve = TagResolver{"yaml"}.lookup
```

Several well-known frameworks and their __struct__ tags are listed at:
https://github.com/golang/go/wiki/Well-known-struct-tags

## Use jsoniter instead of encoding/json {#jsoniter}

*jsoniter* (json-iterator) is a fast and flexible JSON parser available in Java and [Go](https://github.com/json-iterator/go).
It can be used as a drop-in replacement for "__encoding/json__".

In order to build another project, having *gutenfmt* using jsoniter, use the __jsoniter__ build tag as follows:

```shell
go build -tags=jsoniter ./...
```

For building *gutenfmt* as a standalone binary, it is recommended to use it's __Makefile__ and set __GOFLAGS__ accordingly:

```shell
GOFLAGS='-tags=jsoniter' make
```
