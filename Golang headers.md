- `Del` doesnt remove system generated headers
- Need to access the map directly and set to nil

```go
w.Header()["Date"] = nil
```
