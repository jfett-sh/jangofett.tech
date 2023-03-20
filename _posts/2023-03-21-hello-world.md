---
layout: default
title:  "Hello world in golang"
date:   2023-03-21 00:13:42 +0400
categories: posts
---
This is a Go language program that creates a simple web server that listens on port 8080 and responds to any incoming HTTP requests to the root URL ("/") with the message "Hello, world!".

The program imports two packages: "fmt" for formatting and printing text, and "net/http" for creating HTTP servers and handling incoming requests.

{% highlight ruby %}
package main

import (
    "fmt"
    "net/http"
)

func main() {
    http.HandleFunc("/", handler)
    fmt.Println("Listening on port 8080...")
    http.ListenAndServe(":8080", nil)
}

func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello, world!")
}

{% endhighlight %}

The main function first sets up a request handler for incoming requests to the root URL ("/") by calling http.HandleFunc(), which takes two arguments: the URL pattern to match and a function that will be called to handle the request.

The handler function is defined separately and takes two arguments: an http.ResponseWriter to write the response back to the client, and an http.Request containing information about the incoming request.

In the main function, the program then starts the server by calling http.ListenAndServe() with the address to listen on (":8080" in this case) and passing in nil for the second argument, indicating that it should use the default router and request handler.

Finally, the program prints a message to the console indicating that it is now listening for incoming requests.