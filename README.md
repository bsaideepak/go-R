go-R
====

Go(golang) bindings for R language

This is simple binding to eval R expressions and pass results to and from Go code. 

*WARNING!*
Project in the early stage, memory leaks and even SIGFAULTs are possible. Use it on your own risk.

Getting started
====
1. Install R environment: http://cran.r-project.org/
2. Check if you have R header files under correct path(check `#cgo CFLAGS:` directive in sources)
2. Make sure `$R_HOME` s set and pointed to your R location.
3. Install https://github.com/stretchrcom/testify testing package
3. Run `go test` under go-R/R directory

Basic usage
===
```
package main

import (
    "fmt"

    "github.com/nchern/go-R/R"
)

func main() {
    R.Init()

    x := R.NewNumericVector([]float64{1, 2, 3})
    R.SetSymbol("x", x)
    r := R.EvalOrDie("sum(x)").AsNumeric()
    fmt.Println(r.Get(0))
}
```

More examples are in test code.