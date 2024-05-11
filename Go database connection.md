* Sometimes is necessary to run the init function of a package, Without using directly the code. Import it to the blank identifier
```go
import (
 _ "package/import/path"
)
```
* the connection pool don't initializes connections. It's important to test the connection with `db.Ping()`