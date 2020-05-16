
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
  



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgxNTYyNTIyMywyMTAwODA0NTUsLTMzMD
I0ODg2MCwtMTkxNjYxNDc3NSwxNjQ5NDU3NTQyLC0zOTYwODkx
MzAsLTExMTE0MjMzNTEsLTM3NjMwMTQ1MCwtNTgwODM4MzYxLD
k0MDQ1OTY0NSwxMTcwMjg1MTIsLTg2NzI3MzU2OSwxMjI4Mzgz
OTAxLDEzNzg5NzM5OTIsLTQ5MTc0NzQzNSwxMTQzNjM2NDE3LC
04NjIwNDgxMzEsMTc4ODYzNTgyMiwtMTUxNjQ3NDMzNCw3Mzcz
NDg5MDddfQ==
-->