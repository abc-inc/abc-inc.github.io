+++
breadcrumb = ["../:--output", ":text"]
title = "text"
summary = "Name and value pairs, separated by equal sign."
+++

The *text* format organizes the *gutenfmt* output into equal-sign-delimited lines.
It works well for dumping name and value pairs such as environment settings to a file.

## Example: JSON to text

```shell
jq -c -M '.glossary.GlossDiv.GlossList.GlossEntry | del(.GlossDef)' \
  docs/data/glossary.json |
  gutenfmt --output text |
  sort
```

Output:

```text
Abbrev=ISO 8879:1986
Acronym=SGML
GlossSee=markup
GlossTerm=Standard Generalized Markup Language
ID=SGML
SortAs=SGML
```

Note that *jq* has plenty of formatting options, which excel the ones provided by *gutenfmt*.
However, this example illustrates that *gutenfmt* is capable of formatting flat JSON as name and value pairs.
