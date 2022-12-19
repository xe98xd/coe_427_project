package main

import (
	"net/http"
)

func main() {
	ss := &addService{
		cache: map[key]int{},
	}

	m := &subService{
		cache: map[key]int{},
	}

	d := &divService{
		cache: map[key1]float32{},
	}

	ml := &mulService{
		cache: map[key]int{},
	}

	http.HandleFunc("/add", ss.ServeHTTP)
	http.HandleFunc("/sub", m.ServeHTTP)
	http.HandleFunc("/div", d.ServeHTTP)
	http.HandleFunc("/mul", ml.ServeHTTP)
	http.ListenAndServe("localhost:9977", nil)
}
