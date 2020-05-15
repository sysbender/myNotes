
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
	flag bool
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
```

// anonymous type with literal 
e4 := struct{
	flag bool
	counter int16
}{
	flat: true
	counter: 10
}
// conversion

machine word boundary:
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMzMDQzMDk1NCwxMTcwMjg1MTIsLTg2Nz
I3MzU2OSwxMjI4MzgzOTAxLDEzNzg5NzM5OTIsLTQ5MTc0NzQz
NSwxMTQzNjM2NDE3LC04NjIwNDgxMzEsMTc4ODYzNTgyMiwtMT
UxNjQ3NDMzNCw3MzczNDg5MDcsLTg5MzI5ODg5Miw4MjgzODAx
MjRdfQ==
-->