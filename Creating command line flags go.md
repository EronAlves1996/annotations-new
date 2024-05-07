Use `flag.String`.
Important to use `flag.Parse` before using the variables return.

Benefits: you have an automated `-help`

You can use `flag.TypeVar` to explicit store the flag value into a variable