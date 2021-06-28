+++
breadcrumb = ["../:--output", ":tsv"]
title = "tsv"
summary = "Tab-separated name and value pairs (useful for grep, sed, or awk)."
+++

The *tsv* format organizes the *gutenfmt* output into tab-delimited lines.
It works well with traditional Unix text tools such as *grep*, *sed*, and *awk*,
and the text processing performed by *PowerShell*.

## Example: name and value pairs to TSV

```shell
env | grep JAVA | gutenfmt --output tsv
```

Output:

```text
JAVA_HOME	/usr/lib/jvm/java-8-openjdk-amd64
JAVA_OPTS	-server -Xmx512m
```

## Example: compact JSON to TSV

```shell
jq -c -M '.glossary.GlossDiv.GlossList.GlossEntry | del(.GlossDef)' \
  docs/data/glossary.json |
  gutenfmt --output tsv |
  sort
```

Output:

```text
Abbrev  ISO 8879:1986
Acronym SGML
GlossSee        markup
GlossTerm       Standard Generalized Markup Language
ID      SGML
SortAs  SGML
```

Note the difference between *table* and *[tsv]({{< relref "../tsv" >}})*.
*table* aligns the columns using multiple whitespaces,
whereas *tsv* separates them with a single tab character (__'\t'__).
