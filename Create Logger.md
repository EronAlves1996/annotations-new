```go
// Flags are joined using the bitwise operator |.
log.New(stream, prefix, flags)

log.Ldate // Date flag
log.Ltime // time flag
log.Lshortfile // file and line number flag
log.Llongfile // full file path flag

// struct to initialize the server with custom configs
srv := &http.Server {
  Addr: *addr,
  ErrorLog: errorLog,
  Handler: mux
}
```