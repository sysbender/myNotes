
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
```
type example struct{
	flag bool
	counter int16
	pi float32
}
// declare a var, set it zero value
var e example
// literal 
e2 := example{
	flag: true
	counter: 10
	pi : 3.14
}

```

machine word boundary:
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIyODM4MzkwMSwxMzc4OTczOTkyLC00OT
E3NDc0MzUsMTE0MzYzNjQxNywtODYyMDQ4MTMxLDE3ODg2MzU4
MjIsLTE1MTY0NzQzMzQsNzM3MzQ4OTA3LC04OTMyOTg4OTIsOD
I4MzgwMTI0XX0=
-->