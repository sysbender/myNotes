
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

```

machine word boundary:
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzQ2MzYzNTY3LDEyMjgzODM5MDEsMTM3OD
k3Mzk5MiwtNDkxNzQ3NDM1LDExNDM2MzY0MTcsLTg2MjA0ODEz
MSwxNzg4NjM1ODIyLC0xNTE2NDc0MzM0LDczNzM0ODkwNywtOD
kzMjk4ODkyLDgyODM4MDEyNF19
-->