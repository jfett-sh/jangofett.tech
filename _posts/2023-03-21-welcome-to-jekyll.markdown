---
layout: default
title:  "hello world"
date:   2023-03-21 00:13:42 +0400
categories: posts
---
hey there

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
