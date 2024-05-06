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