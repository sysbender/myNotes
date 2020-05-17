
# reference
 

*   Go Language Programming Practical Basics Tutorial 
* 

# installation

go env
go get
go run main.go
go install

# workspace


set GOPATH=C:\Users\jason\go

```
go-workspace
	bin
	src
		github.com
			sysbender
				myproject1
					project_files
	pkg
```

# variable

```
string
bool
int int8 int16 int32 int64
uint uint8 uint16 uint32 uint64 uintptr
byte = uint8
rune = uint32
float32 float64
complex64 complex128
```
var will zero the variable
goLang use conversion over casting.
## struct
```go
type example struct{
	flag bool   //machine word boundary:
	counter int16
	pi float32
}


// declare a var, set it zero value
var e example
// literal construction : not zero
e2 := example{
	flag: true
	counter: 10
	pi : 3.14
}
// pass zero parameter with literal construction
func foo(example{}){}

// anonymous type
var e3 struct{
	flat bool
	counter int16
}
fmt.Printf("%+v\n", e3)

// anonymous type with literal 
e4 := struct{
	flag bool
	counter int16
}{
	flat: true
	counter: 10
}
// conversion explicitly
// var1 type1 = type1(var2 type2 )

```

## pointer
pass by value
* thread - os
* p
* goroutine - stack 2k, 
* echo func - has a memory frame to access


* data segment
* stack - 1Mbytes
* heap

### factory function
like constructor, return an object
* value semantic
* pointer semantic - not using during construction
escape analysis: find out which pointer go to head/stack, avoid integrate issue
  

### stack growth
* stack is about 2K for go routine. if it is not enough, it will be copied and moved to a new consecutive place with a 25% percent bigger size.
* heap using for any value that will be shared across go-routine boundaries
* any value that don't know the size at compile time

### garbage collection
tri-color, pacing algorithm , 
*  up to 25% cpu
* GOGC = 100% , up to top
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQxNzIwNDQ2NiwtMTE4OTk5MDg3MiwtMT
ExNzQzMDIxMCwxMjkxNjQ2MzQ5LDE4MTU2MjUyMjMsMjEwMDgw
NDU1LC0zMzAyNDg4NjAsLTE5MTY2MTQ3NzUsMTY0OTQ1NzU0Mi
wtMzk2MDg5MTMwLC0xMTExNDIzMzUxLC0zNzYzMDE0NTAsLTU4
MDgzODM2MSw5NDA0NTk2NDUsMTE3MDI4NTEyLC04NjcyNzM1Nj
ksMTIyODM4MzkwMSwxMzc4OTczOTkyLC00OTE3NDc0MzUsMTE0
MzYzNjQxN119
-->