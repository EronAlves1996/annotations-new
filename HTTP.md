 * `409: CONFLICT`: used when Unique is violated (indicates the actual solicitation has conflicted with another resource)
 * Normally, we use `204` for delete operations. `204` is used every time we don't have any body to return in response to the request
 * If you prefix the URL with HTTPS, but the server don't have any SSL or TLS configuration, you cannot connect for it because the client (when well coded) will think that it's a SSL connection and try to decode it
## HTTP2

* Headers are always in lowercase
