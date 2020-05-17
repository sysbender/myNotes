
# reference
 

*   Go Language Programming Practical Basics Tutorial 
* 

##  big points
-   Remember LESS is MORE.
    
-   `readability`  = not hiding the cost;  `simplicity`  = hide complexity
    
-   If you don't UNDERSTAND the  `DATA`, you DON'T UNDERSTAND the PROBLEM you're working on.
    
-   Remember:  `stack`  (stay on stack) vs  `heap`  (share on heap)
    
-   Take command of  `type`  & Take command of  `semantics`
    
-   Mantra: REDUCE, MINIMIZE, SIMPLIFY.
    
-   Never share a string or slice  `unless`  you're marshaling or unmarshaling.
    
-   Small is fast = because smaller data structures can stay within the cachelines.
    
-   Memory leak in go: a reference on the heap that  `isn't garbage collected`  AND  `not being used`.
    
-   It's never a good reason to alter a data set after you pull it!
    
-   Know your length when getting a slice of a slice.
    
-   (Big NO NO) Don't mix  `value semantics`  WITH  `pointer semantics`; vice versa.
    
-   When in doubt USE  `pointer semantics`; except with time.
    
-   Method sets dictate interface compliance.
    
-   We do not use embedding to reuse state! We use embedding to reuse behavior. (WE EMBED BECAUSE WE NEED BEHAVIOR)
    
-   Group by behavior (by things that they do vs. what they are).
    
-   There is implicit conversion in go with interface types because they are valueless and same memory model.
    
-   Always  `return`  the  `error`  interface type
    
-   Don't use  `pointer semantics`  when dealing with  `error`  handling, because the addresses are always different.
    
-   You are not allowed to both: log an  `error`  && pass it up.
    
-   You are not allowed to create a  `go routine`  unless you can determine WHEN and HOW it will be terminated
    
-   Do not think of channels as queues, but as  `signals`.
    
-   Don't use a buffer larger than 1; Anything more and it's unsafe.
    
    -   Using  `<=1`  = somewhat of a garuntee.
    -   Easier to catch problems/bugs.



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
 
# data structure

## data oriented design
## array
## slices
## map


<!--stackedit_data:
eyJoaXN0b3J5IjpbNjkzNDY0MDQyLDE5NjEwNjA1MiwtMTY1Nz
YyMDgyNiwtMTE4OTk5MDg3MiwtMTExNzQzMDIxMCwxMjkxNjQ2
MzQ5LDE4MTU2MjUyMjMsMjEwMDgwNDU1LC0zMzAyNDg4NjAsLT
E5MTY2MTQ3NzUsMTY0OTQ1NzU0MiwtMzk2MDg5MTMwLC0xMTEx
NDIzMzUxLC0zNzYzMDE0NTAsLTU4MDgzODM2MSw5NDA0NTk2ND
UsMTE3MDI4NTEyLC04NjcyNzM1NjksMTIyODM4MzkwMSwxMzc4
OTczOTkyXX0=
-->