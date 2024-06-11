* Create Logger
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

* Using command line flags
	Use `flag.String`.
	Important to use `flag.Parse` before using the variables return.
	
	Benefits: you have an automated `-help`
	
	You can use `flag.TypeVar` to explicit store the flag value into a variable