# A Little Go App

# 1: Web Clients

In this section you're going to learn the basics to write a web servers and clients in Go.

The `net/http` package provides a series of functions and types to help you sending HTTP requests.
The most important types are:

- the [Client](https://golang.org/pkg/net/http#Client)
- the [Request](https://golang.org/pkg/net/http#Client)
- the [Response](https://golang.org/pkg/net/http#Response)

We'll get to see how those types work in a minute!
But before that it is important to realise that there are helper functions that will make our life easier here too.

## The Get method

One of those helper functions is [`Get`](https://golang.org/pkg/net/http#Get).

```go
package main

import (
        "fmt"
        "log"
        "net/http"
)

func main() {
        res, err := http.Get("https://golang.org")
        if err != nil {
                log.Fatal(err)
        }
        fmt.Println(res.Status)
}
```
[source code](examples/get.go)

This program will send a GET HTTP request to the Go homepage and will print the status code of the response,
unless something goes wrong in which case it will log the error and stop the execution of the program.

Try changing the value of the URL to see what other codes you're able to get.
Some ideas you could try:

- https://golang.org/foo
- http://thisurldoesntexist.com
- https:/thisisnotaurl

Let's move on to the next [section][1]!

[1]: ../Section2-Server/README.md
