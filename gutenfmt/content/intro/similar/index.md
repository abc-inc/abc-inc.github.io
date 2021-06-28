+++
title = "Similar Projects"
+++

The following list contains Go libraries (in alphabetic order) with similar features:

## Libraries

- https://github.com/juju/cmd - lightweight abstraction, comes with three formatters
- https://github.com/drewstinnett/go-output-format - comprehensive library, lots of features
- https://github.com/thediveo/klo - comprehensive library, lots of features

## Feature Comparison

| Feature                 | gutenfmt (CLI)     | gutenfmt (lib)     | cmd                | go-output-format   | klo                |
|-------------------------|:------------------:|:------------------:|:------------------:|:------------------:|:------------------:|
| Output CSV              |                    | :heavy_check_mark: |                    |                    |                    |
| Output JSON             | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Output JSON (pretty)    | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    |
| Output Table            | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :heavy_check_mark: |
| Output Template         |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |
| Output Text             | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |
| Output TSV              | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    |
| Output YAML             | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Output YAML (pretty)    | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    |
| Output "Smart" (detect) |                    |                    | :heavy_check_mark: |                    |                    |
| Query with JSONPath     |                    |                    |                    | :heavy_check_mark: | :heavy_check_mark: |
| Sorting                 |                    | :wavy_dash:        |                    |                    | :heavy_check_mark: |

If you know a similar project, or the feature comparison is outdated, please submit a pull request.

## Applications supporting different output formats

The following applications implement similar functionality.
However, they contain application specific code or dependencies, which might make it difficult to use them as a library.
In other words, they are primarily meant to be a source for inspiration.

- https://github.com/arduino/arduino-cli - minimal implementation with some dependencies
- https://github.com/cli/cli - smart way of enabling JSON and template-based output
- https://github.com/hashicorp/vault/ - a vault-specific abstraction for three different formats

