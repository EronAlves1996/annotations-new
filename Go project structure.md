https://github.com/thockin/go-build-template

As a general, have a `cmd` for binaries, a `internal` for internal code, and a `ui` for static web assets.

* Internal has special meaning. It means that only the actual module can use this directory code. No other can