+++
breadcrumb = ["../:--output", ":json"]
title = "json"
summary = "JSON string. This setting is the default for non-terminals."
+++

[JSON](https://json.org/) is the default output format of *gutenfmt*.
Most programming languages can easily decode JSON strings using built-in functions or with publicly
available libraries.

For more advanced filtering, you can consider *jq*, a command line JSON processor.
You can download it and find the official tutorial at https://stedolan.github.io/jq/.

## Example: name and value pairs to compact JSON

The following example displays the Java environment variables in the default JSON format.

```shell
env | grep JAVA | gutenfmt --output json
```

Output:

```text
{"JAVA_HOME":"/usr/lib/jvm/java-8-openjdk-amd64","JAVA_OPTS":"-server -Xmx512m"}
```
