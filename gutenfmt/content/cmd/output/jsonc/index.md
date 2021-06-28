+++
breadcrumb = ["../:--output", ":jsonc"]
title = "jsonc"
summary = "Colorized JSON. This setting is the default for interactive terminals."
+++

[JSON](https://json.org/) has a compact format, which is difficult to read.
The *jsonc* format applies syntax highlighting of JSON tokens and indentation.

## Example: name and value pairs to formatted JSON

```shell
env | grep JAVA | gutenfmt --output jsonc
```

Output:

```json
{
  "JAVA_HOME": "/usr/lib/jvm/java-8-openjdk-amd64",
  "JAVA_OPTS": "-server -Xmx512m"
}
```

## Example: compact JSON to formatted JSON

```shell
jq -c -M . docs/data/glossary.json | gutenfmt --output jsonc
```

Output:

```json
{
  "glossary": {
    "GlossDiv": {
      "GlossList": {
        "GlossEntry": {
          "Abbrev": "ISO 8879:1986",
          "Acronym": "SGML",
          "GlossDef": {
            "GlossSeeAlso": [
              "GML",
              "XML"
            ],
            "para": "A meta-markup language, used to create markup languages such as DocBook."
          },
          "GlossSee": "markup",
          "GlossTerm": "Standard Generalized Markup Language",
          "ID": "SGML",
          "SortAs": "SGML"
        }
      },
      "title": "S"
    },
    "title": "example glossary"
  }
}
```

Note that *jq* has plenty of formatting options, which excel the ones provided by *gutenfmt*.
However, this example illustrates that *gutenfmt* is capable of formatting complex JSON prettily.
