+++
breadcrumb = ["../:--output", ":table"]
title = "table"
summary = "ASCII table."
+++

The *table* format produces human-readable representations of *gutenfmt* output in a tabular form.

## Example: name and value pairs to table

```shell
env | grep JAVA | gutenfmt --output table
```

Output:

```text
JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64 
JAVA_OPTS -server -Xmx512m                  
```

## Example: compact JSON to table

```shell
jq -c -M '.glossary.GlossDiv.GlossList.GlossEntry | del(.GlossDef)' \
  docs/data/glossary.json |
  gutenfmt --output table |
  sort
```

Output:

```text
Abbrev    ISO 8879:1986
Acronym   SGML
GlossSee  markup
GlossTerm Standard Generalized Markup Language
ID        SGML
SortAs    SGML
```

Note the difference between *table* and *[tsv]({{< relref "../tsv" >}})*.
*table* aligns the columns using multiple whitespaces,
whereas *tsv* separates them with a single tab character (__'\t'__).
