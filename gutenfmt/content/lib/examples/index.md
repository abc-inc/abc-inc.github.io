+++
title = "Examples"
toc = true
+++

The examples listed on this page use the following model:

```go
type User struct {
	Name     string `json:"username" yaml:"Username"`
	Mail     string `json:"email" yaml:"E-Mail"`
	Password string `json:"-" yaml:"-"`
}

type Team struct {
	name    string
	members []User
}
```

## JSON with custom Formatter

Note that __Team__ does not have any field tags.
Thus, a custom __Formatter__ is required in order to obtain a proper string representation.
Moreover, it prints the number of __Team__ members instead of enumerating them.

```go
w := NewJSON(os.Stdout)
w.Formatter.SetFormatterFunc(reflect.TypeOf(t).Name(), func(i interface{}) (string, error) {
	tm := i.(Team)
	return `{"team":"` + tm.Name() + `","members":` + strconv.Itoa(len(tm.Members())) + `}`, nil
})

n, err := w.Write(t)
// Output:
// {"team":"SUPPORT","members":2}
```

## Table from single struct/map

By default, the table representation of a __struct__ is a two-column newline-separated string.
The columns are aligned, which results in a human-readable table.

```text
firstFieldName  value1
secondFieldName value2
```

A __map__ is handled similarly.
Each entry in the __map__ corresponds to a row in the table representation.

```go
w := NewTab(os.Stdout)
n, err := w.Write(u)
// Output:
// username John Doe
// email    john.doe@local
}
```

## Table from slice of structs/maps

When writing a __struct__ or __map__ slice, the table layout is changed accordingly.
Every element in the slice corresponds to a row of multiple columns.

```go
w := NewTab(os.Stdout)
n, err := w.Write(users)
// Output:
// username       email
// John Doe       john.doe@local
// Rudolf Lingens rudolf.lingens@local
```

## YAML from slice of structs/maps

When formatting a __struct__, __map__ or a slice thereof to YAML,
the "__yaml__" field tags are considered instead.
This enables to have a different naming for JSON and YAML output.
Moreover, certain fields could be excluded by using the field tag __"-"__.

```go
w := NewYAML(os.Stdout)
_, _ = w.Write(users)
// Output:
// - Username: John Doe
//   E-Mail: john.doe@local
// - Username: Rudolf Lingens
//   E-Mail: rudolf.lingens@local
```
