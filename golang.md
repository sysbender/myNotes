
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

machine word boundary:
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE3MDI4NTEyLC04NjcyNzM1NjksMTIyOD
M4MzkwMSwxMzc4OTczOTkyLC00OTE3NDc0MzUsMTE0MzYzNjQx
NywtODYyMDQ4MTMxLDE3ODg2MzU4MjIsLTE1MTY0NzQzMzQsNz
M3MzQ4OTA3LC04OTMyOTg4OTIsODI4MzgwMTI0XX0=
-->