Go support for EDF+
===================

This package provides a [Go](https://golang.org/) implementation of the EDF format. It reads EDF+ files into two structures:

+ A map from strings to strings, representing the main header in the EDF file.
+ A slice of slices of int16, each one representing one channel's recording.

They can be accessed using the `ReadFile(string)` function. The header information can be accessed through the keys given by the `GetSpecsList()` function. This query will give the raw string contained in the EDF file to be processed. The records can be accessed through their label's index. They are stored in their raw form. They can be converted using their respective convertion factor, as given by the `SetConvertionFactor(map[string]string)` function.

Getting started
---------------

To install the EDF lib, run on terminal:

```
go get github.com/ishiikurisu/edf
```

Then import it on your code:

``` go
import "github.com/ishiikurisu/edf"
import "fmt"

func main() {
    edfFile := "your_file.edf"
    header, records := edf.ReadFile(edfFile)
    fmt.Println(edf.WriteCSV(header, records))
}
```
