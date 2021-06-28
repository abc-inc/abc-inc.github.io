+++
breadcrumb = ["../:--output", ":yamlc"]
title = "yamlc"
summary = "Colorized YAML."
+++

The *yamlc* format applies syntax highlighting of YAML tokens.

## Example: name and value pairs to formatted YAML

```shell
env | grep JAVA | gutenfmt --output yamlc
```

Output:

```yaml
JAVA_HOME: /usr/lib/jvm/java-8-openjdk-amd64
JAVA_OPTS: -server -Xmx512m
```

## Example: compact JSON to formatted YAML

```shell
jq -c -M . docs/data/glossary.json | gutenfmt --output yamlc
```

Output:

```yaml
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
