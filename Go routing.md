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