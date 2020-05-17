
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
STW - stop the world
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NTc2MjA4MjYsLTExODk5OTA4NzIsLT
ExMTc0MzAyMTAsMTI5MTY0NjM0OSwxODE1NjI1MjIzLDIxMDA4
MDQ1NSwtMzMwMjQ4ODYwLC0xOTE2NjE0Nzc1LDE2NDk0NTc1ND
IsLTM5NjA4OTEzMCwtMTExMTQyMzM1MSwtMzc2MzAxNDUwLC01
ODA4MzgzNjEsOTQwNDU5NjQ1LDExNzAyODUxMiwtODY3MjczNT
Y5LDEyMjgzODM5MDEsMTM3ODk3Mzk5MiwtNDkxNzQ3NDM1LDEx
NDM2MzY0MTddfQ==
-->