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

## Basic HTTP Server Schema

```go
package main

import (

"log"

"net/http"

)

// Define a home handler function which writes a byte slice containing

// "Hello from Snippetbox" as the response body.

func home(w http.ResponseWriter, r *http.Request) {
	w.Write([]byte("Hello from Snippetbox"))
}

func main() {
	
	// Use the http.NewServeMux() function to initialize a new servemux, then
	
	// register the home function as the handler for the "/" URL pattern.
	
	mux := http.NewServeMux()
	
	mux.HandleFunc("/", home)
	
	// Use the http.ListenAndServe() function to start a new web server. We pass in
	
	// two parameters: the TCP network address to listen on (in this case ":4000")
	
	// and the servemux we just created. If http.ListenAndServe() returns an error
	
	// we use the log.Fatal() function to log the error message and exit. Note
	
	// that any error returned by http.ListenAndServe() is always non-nil.
	
	log.Println("Starting server on :4000")
	
	err := http.ListenAndServe(":4000", mux)
	
	log.Fatal(err)

}
```

* The `/` is a catch all handler for servemux
* Format for TCP address listen is `host:port`
  - Omitting the `host` part means listen in all network interfaces (ipv4, ipv6, etc)
  - Port can be specified with a name defined in `/etc/services` file (`:http`, `https`)

## Capitalizing a word

```go
strings.Title(w)
```

## Checking error types

Use `errors.Is`

## Database connection

* Sometimes is necessary to run the init function of a package, Without using directly the code. Import it to the blank identifier
```go
import (
 _ "package/import/path"
)
```
* the connection pool don't initializes connections. It's important to test the connection with `db.Ping()`
## Default servermux

- if you don't use a servermux, and register directly to the http package, you gonna register to the default servermux
- don't recommendable for production, because it is a global variable (any package can register on it)
## Error Handling

* Its recommended to panic/exit only on main function
* Return errors
- In web application, errors are produced by simple functions
- Functions return a tuple, when one is a error
- You can use a function to produce custom error output
- practice: use a helpers file to define error handling code 

## Env vars

```go
// get an env var from system 
os.GetEnv()
```

## Handle vs Handlefunc

* Handle is supposed to accept an object that implements the interface on its second argument
* If an object is not required, and just a stateless function, use HandleFunc

## Serving files over http

Use http fileserver, passing a http Dir

## Initialize module

```sh
$ go mod init <module-path>
```

## Map

```go
// declaration
map[key]value

// initialization
make(map[key]value)

// another way of init
map[key]value{}

// puting a value
map["asja"] = "Some value"

// getting a value, if not present, returns nil or zeroed value
v := map["asja"]

// second way, the second value represents the success of 
// getting the value
m, ok := map["asja"]

// iterating over key/values
for k, v := range map {
  // make anything to them
}

// getting length of values
len(map)

// deleting a value
delete(m, key)
```

## Max Int

```go
math.MaxInt
```

## Module Path

- should be a unique string
- I follow the rule of a GitHub url that I learned before, but as a general rule, it can be a domain url that you own (what makes sense)
## Modules security

- Use `go mod verify` to verify the packages against the go.sum
- use `go mod download` to download the dependencies of the module
- Use the `-u` flag in go get to update the package 
  - Without the version spec, it updates to lastest minor/patch available
  - To specify some version, append and `@x.xx.xx` 
- Use `go mod tidy -v` to remove any unused packages
- Use `go get` with a `none` version spec to remove the package 

## Project Structure

https://github.com/thockin/go-build-template

As a general, have a `cmd` for binaries, a `internal` for internal code, and a `ui` for static web assets.

* Internal has special meaning. It means that only the actual module can use this directory code. No other can
* For web, handlers come in web dir on cmd

## Response Writer

- it's possible to call whitehead once per response 
- if write is called before, it assumes 200, and it's immutable after it
- writeHeader should be called before these two methods
- http.Error is a shortcut to send errors

## Routing

* fixed paths 
  - Matches exactly the route
- subtree paths
  - Matches the route and sub routes
  - ends with a trailing slash `/`
* Ensuring a subtree path to act like a fixed path
```go
package main

...

func home(w http.ResponseWriter, r *http.Request) {

// Check if the current request URL path exactly matches "/". If it doesn't, use

// the http.NotFound() function to send a 404 response to the client.

// Importantly, we then return from the handler. If we don't return the handler

// would keep executing and also write the "Hello from SnippetBox" message.

if r.URL.Path != "/" {

http.NotFound(w, r)

return

}

w.Write([]byte("Hello from Snippetbox"))

}

...
```

- longer patterns take precedence over the shortest
- req urls are automatically sanitized 
- hostname matching
  - useful for subhosts, like `foo.localhost.com`

```
It’s important to acknowledge that the routing functionality provided by Go’s servemux is

pretty lightweight. It doesn’t support routing based on the request method, it doesn’t

support clean URLs with variables in them, and it doesn’t support regexp-based patterns. If

you have a background in using frameworks like Rails, Django or Laravel you might find this a

bit restrictive… and surprising!
```

## Serving static assets
```go
mux.Handle("/static/", http.StripPrefix("/static/", http.FileServer(http.Dir("./ui/static"))))
```

## Slices


Iterating

```go
for k,v := range slice {
  // code
}
```

## Sorting

```go
// slice of int
sort.Ints(slc)
```

## SQL Nulls

- Go is not good to handling null values on database 
- you can use sql.Null* to use in place to unmarshal the value
- However, the best thing to do is to avoid the nil values, by not permitting them to occur on SQL columns 
## SQL Row scanning

It's very important to call rows.Err after the iteration to check for erros on iteration.
Always do that 


## String

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

## Template errors

* `ERROR   2024/05/13 22:21:37 helpers.go:11: html/template:base: ends in a non-text context: {stateRCDATA delimNone urlPartNone jsCtxRegexp attrNone elementTextarea <nil>}`
	* https://github.com/golang/go/issues/20773#issuecomment-671177435

## Ternary Operator
* It dont haves

## Type assertion

```go
v, ok := x.(type)
```

## Type conversion

Str to int
```go
n, err := strconv.Atoi(str)
```

numb to str
```go
v := fmt.Sprint(n)
```

## Headers

- `Del` doesnt remove system generated headers
- Need to access the map directly and set to nil

```go
w.Header()["Date"] = nil
```

## Initializing a buffer

```go
bf := new(bytes.Buffer)
```

## Passing data to templates

- You can pass one and only struct to templates
- Compose structs to pass a single struct, then
