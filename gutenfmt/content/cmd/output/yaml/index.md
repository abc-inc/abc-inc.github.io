+++
breadcrumb = ["../:--output", ":yaml"]
title = "yaml"
summary = "YAML, a machine-readable alternative to JSON."
+++

[YAML](https://yaml.org/) is a good choice for handling the output programmatically with services
and tools that emit or consume YAML-formatted strings.

For more advanced filtering, you can consider *yq*, a command line YAML processor.
You can download it and find documentation at https://mikefarah.gitbook.io/yq/.

## Example: name and value pairs to YAML

```shell
env | grep JAVA | gutenfmt --output yaml
```

Output:

```text
JAVA_HOME: /usr/lib/jvm/java-8-openjdk-amd64
JAVA_OPTS: -server -Xmx512m
```

## Example: compact JSON to YAML

```shell
jq -c -M . docs/data/glossary.json | gutenfmt --output yaml
```

Output:

```text
glossary:
    GlossDiv:
        GlossList:
            GlossEntry:
                Abbrev: ISO 8879:1986
                Acronym: SGML
                GlossDef:
                    GlossSeeAlso:
                        - GML
                        - XML
                    para: A meta-markup language, used to create markup languages such as DocBook.
                GlossSee: markup
                GlossTerm: Standard Generalized Markup Language
                ID: SGML
                SortAs: SGML
        title: S
    title: example glossary
```
