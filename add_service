package main

import (
	"fmt"
	"net/http"
	"strconv"
)

// /add
type AddService interface {
	PostSum(x int, y int)
	GetSum(x int, y int) (sum int)
	PutSum(x int, y int)
	DeleteSum(x int, y int)
}

func (ss *addService) PostSum(x int, y int) {

	ss.cache[key{x, y, 0}] = x + y
}

func (ss *addService) GetSum(x int, y int) (sum int) {

	sum, exists := ss.cache[key{x, y, 0}]
	if !exists {
		return -1
	}
	return
}

func (ss *addService) DeleteSum(x int, y int) {
	delete(ss.cache, key{x, y, 0})
}

func (ss *addService) ServeHTTP(w http.ResponseWriter, r *http.Request) {
	num1 := r.URL.Query()["x"][0]
	num2 := r.URL.Query()["y"][0]
	x, _ := strconv.Atoi(num1)
	y, _ := strconv.Atoi(num2)

	switch r.Method {
	case "POST":
		ss.PostSum(x, y)
		fmt.Fprintf(w, "New sum saved!")
	case "GET":
		sum := ss.GetSum(x, y)
		if sum == -1 {
			fmt.Fprintf(w, "Sum does not exist in cache!")
		} else {
			fmt.Fprintf(w, "Sum = %v", sum)
		}
	case "PUT":
	case "DELETE":
		ss.DeleteSum(x, y)
		fmt.Fprintf(w, "Sum deleted!")
	default:
		fmt.Fprintf(w, "Unsupported HTTP method!")
	}
}
