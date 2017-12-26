# Go
Go ([golang.org](https://golang.org/)) is a statically typed, garbage collected compiler language mostly used in backend development.

- File extension: ```**/*.go```

## Get Started

### [Setup](https://golang.org/doc/install)

### REPL
Go does not natively provide you with a REPL. 3rd party solutions exit (e.g. [gore](https://github.com/motemen/gore)).

### Compile
```shell
go build -o ./bin/main ./src
```

This outputs an executable.

- Ignored test files: ```**/*_test.go```

## Tooling
TODO

### Project creation
TODO

### Package management
TODO

### Testing & Linting
TODO

## Hello World
```go
package main

import "fmt"

func main() {
  fmt.Printf("Hello, world!\n")
}
```

## Basics
- Do not use semicolons
- Chars can be denoted using ``` '' ```
- Strings can be denoted using ``` "" ```
- Underscores (``` _ ```) can be used as placeholders for unused values

- ```main``` function (from ```main``` package) is called on execution

- Do use ```camel case``` (```mixedCaps```/```MixedCaps```)

### Comments
```go
// Single line

/* Multi
line */
```

### Variables
```go
// Mutable binding with type
var variableName int
var variableName, variableName2 int

// Mutable binding with type and initialization
var variableName int = 0
var variableName, variableName2 int = 0, 0

// Types can be inferred
var variableName = 0
var variableName, variableName2 = 0, 0

func main() {
  // Short variable declarations with implicit type (can only be used inside of functions)
  variableName := 0
}

// Constants
const constantName = 0
```

### Data types
TODO

Go is statically typed.

#### Primitives
- Boolean: ```bool```
- Byte (alias for ```uint8```): ```byte```
- Integer (```int```: signed, ```uint```: unsigned):
  - 8-bit: ```int8```/```uint8```
  - 16-bit: ```int16```/```uint16```
  - 32-bit: ```int32```/```uint32```
  - 64-bit: ```int64```/```uint64```
  - architecture: ```int```/```uint```
- Floating-point: ```float32``` and ```float64```
- Complex: ```complex64``` and ```complex128```
- Character (alias for ```int32```, represents a Unicode code point): ```rune```
- String: ```string```

#### Strings
Go's strings are treated like primitives.

#### Generics
Go does not have generics.

#### Interfaces
In Go an interface defines a set of method signatures.  
Any value that implements these methods will be accepted.

```go
type InterfaceName interface {
  MethodName() int
}
```

The empty interface (```interface{}```) may hold values of any type.

#### Null
- ```nil```

#### Type checks
TODO

### Functions
```go
// Function declarations
func functionName(param int, param2 int) int {
  // Statements go here
  return param2
}

// Multiple return values
func functionName(param, param2 int) (int, int) {
  // Statements go here
  return param, param2
}

// Named return values ("naked" return)
func functionName(param, param2 int) (param, param2 int) {
  // Statements go here
  return
}

// Function calls
returnValue := functionName(0, 0)
// Function calls with multiple return values
returnValue, returnValue2 := functionName(0, 0)
```

### Flow control

#### If/else
```go
// If (simple)
if condition { /* Statements go here */ }

// If with short statement
if variableName := 0; variableName == 0 {
  // Statements go here
}

// If/else-if/else
if condition {
  // Statements go here
} else if condition2 {
  // Statements go here
} else {
  // Statements go here
}
```

#### Conditional expression
Go does not have the ```?:``` ternary operator.

#### Switch
```go
// Switch (simple) - automatically breaks after first matching case
switch value {
  case comparedValue:
    // Statements go here

  case comparedValue2:
    // Statements go here

  default:
    // Statements go here
}

// Switch with short statement
switch variableName := 0; variableName {/*...*/}

// Switch as if/else-if/else
switch {
  case condition:
    // Statements go here

  case condition2:
    // Statements go here

  default:
    // Statements go here
}
```

#### Loops

##### Forever
```go
for {
  // Statements go here
}
```

##### Conditional
```go
// While-like loop
for condition {
  // Statements go here
}
```

##### Count
```go
for count := 0; count < 10; count++ {
	// Statements go here
}
```

##### Iterate data
```go
// Array for-each
for index, currentValue := range arrayName {
  // Statements go here
}
```

Stop a loop using ```break```, skip an iteration using ```continue```.

### Data Structures

#### Tuples
Use arrays.

#### Arrays
Go's arrays are statically-sized.

```go
// Declare array
var arrayName [10]int
var arrayName [3]int{0, 1, 2}
arrayName := [3]int{0, 1, 2}

// Access array value
value := arrayName[index]

// Mutate array value
arrayName[index] = value

// Get array length
length := len(arrayName);
```

#### Array slices
Go's array slices can be thought of as dynamically-sized views into arrays.

```go
// Create slice from array
var sliceName []int = arrayName[0:1] // Slice including the first element of array 'arrayName'
var sliceName []int = arrayName[0:4] // Slice including all elements of array 'arrayName'
var sliceName []int = arrayName[:4] // Slice including all elements of array 'arrayName'
var sliceName []int = arrayName[0:] // Slice including all elements of array 'arrayName'
var sliceName []int = arrayName[:] // Slice including all elements of array 'arrayName'

// Slice literals
sliceName := []int{0, 1, 2, 3}

// Create slice with 'make'
sliceName := make([]int, 4) // length = 4, capacity = 4
sliceName := make([]int, 0, 4) // length = 0, capacity = 4

// Get slice length and capacity
length := len(sliceName) // Number of elements in the slice
capacity := cap(sliceName) // Number of elements in the underlying array, counting from lower slice bound

// Append to slice
append(sliceName, sliceName2/*, sliceName3, sliceNameN*/)
```

#### Generic Objects
Use maps or structs.

#### Structs
```go
// Declare struct type
type StructTypeName {
  key int
  key2 int
}

type StructTypeName {
  key, key2 int
}

// Create new struct
structName := StructTypeName{0, 1}
structName := StructTypeName{key2: 0} // key: 0 is implicitly
// Anonymous struct type
structName := struct {key, key2 int}{0, 1}

// Access struct value
value := structName.key2

// Mutate struct value
structName.key2 = value
```

#### Maps
```go
// Create new map
var mapName map[string]int
mapName := make(map[string]int)
mapName := map[string]int{
  "key": 0,
  "key2": 1,
}

// Access map value
value := mapName["key2"]
value, exists := mapName["key2"] // Check if key exists in map

// Mutate map value
mapName["key2"] = value

// Delete map key
delete(mapName, "key2")
```

### Classes/methods
Go does not have classes (use structs).  
However, it is possible to define methods on types.

```go
type StructTypeName struct { key, key2 int }

// Declare method with value receiver
func (receiverParam StructTypeName) methodName(param, param2 int) int {
  return receiverParam.key2 + param2
}

// Declare method with pointer receiver (enables modification of received value + more performant)
func (receiverParam *StructTypeName) methodName(param, param2 int) int {
  return receiverParam.key2 + param2
}

structName := StructTypeName{0, 1}

// Call method
structName.methodName(0, 1) // returns 2
```

### Memory management
Go is garbage collected. Manual memory management is neither required nor possible.

#### Pointers & references
Go has pointers.

> [The type ```*T``` is a pointer to a ```T``` value.](https://tour.golang.org/moretypes/1)  
> [The ```&``` operator generates a pointer to its operand.](https://tour.golang.org/moretypes/1)  
> [The ```*``` operator denotes the pointer's underlying value. [...] This is known as "dereferencing" or "indirecting".](https://tour.golang.org/moretypes/1)

```go
var pointerName *int // Pointer
var variableName int

// Create pointer
pointerName = &variableName2

// Access pointer's underlying value
value := *pointerName

// Mutate pointer's underlying value
*pointerName = value
```

Note: Out of convenience, writing ```(*structName).key2``` is equivalent to ```structName.key1```.

### Modules
A Go program is made up of packages. The program starts in the ```main``` package.  
Additional packages can be imported from there.

> [By convention, the package name is the same as the last element of the import path. For instance, the "math/rand" package comprises files that begin with the statement package rand.](https://tour.golang.org/basics/1)

Local packages can be imported using their relative path (e.g. ```'./package'```, ```'../package'```).
External packages imported using the name (e.g. ```'module'```, ```'module/sub'```).

Each package can consist of multiple files. Just add the same ```package <name>``` line to the top of each file and the contained code will be treated as if it was part of the same file.

```go
// Import
import "package"

import (
  "package"
  "package/sub"
)

// Declare packages
package name

// Export: In Go names are automatically exported if they begin with a capital letter
```

### Concurrency

#### Goroutines
Goroutines are lightweight threads.

You can start a new goroutine with the ```go``` keyword:
```go
go functionName()
```

#### Channels
Go's channels enable easy synchronization and communication between goroutines.  
They are a ["typed conduit"](https://tour.golang.org/concurrency/2) through which values can be sent and received.

Channels can be buffered (but don't have to).
Sending to a buffered channel blocks if the buffer is full.
Reading from one blocks if it is empty.

```go
// Create a new (unbuffered) channel
channelName := make(chan int)

// Create a new buffered channel
channelName := make(chan int, 100) // Second argument is the buffer length

// Send to channel
channelName <- value

// Receive from channel
value := <-channelName
```

##### Select

#### Mutexes

## Special features

### Deferred statements (in functions)
TODO
