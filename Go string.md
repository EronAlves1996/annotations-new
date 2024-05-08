Iterating

```go
for k, v := range str {
	// v stands for rune type
	// to use as string
	string(v)
	// k stands for position
}
```

Using a replacer

```go
import "strings"

var dnaReplacer *strings.Replacer = strings.NewReplacer(
  "A", "T",
  "T", "A",
  "C", "G",
  "G", "C",
)

func DNAStrand(dna string) string {
  return dnaReplacer.Replace(dna)
}
```
