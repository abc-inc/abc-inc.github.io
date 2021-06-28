+++
title = "Go Library"
+++

### Basic Usage

The following program parses JSON input and formats it as table:

```go
package main

import (
	"encoding/json"
	"log"
	"os"

	"github.com/abc-inc/gutenfmt/gfmt"
)

func main() {
	d := json.NewDecoder(os.Stdin)
	var m map[string]interface{}
	if err := d.Decode(&m); err != nil {
		log.Fatal("cannot decode JSON input", err)
	}
	
	w := gfmt.NewTab(os.Stdout)
	if _, err = w.Write(m); err != nil {
		log.Fatal("cannot write table", err)
	}
}
```
