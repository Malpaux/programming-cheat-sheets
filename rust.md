# Rust
Rust ([rust-lang.org](https://www.rust-lang.org/en-US/)) is a statically typed systems programming language with guaranteed thread/memory safety.

- File extensions: ```**/*.rs```, ```**/*.rc``` (deprecated)

## Get started

### [Setup](https://www.rust-lang.org/en-US/install.html)

### REPL
Rust does not natively provide you with a REPL. 3rd party solutions are experimented on (e.g. [Rusti](https://github.com/murarth/rusti)).

### Compile
```shell
rustc main.rs
```

Build a ```crate``` (project)
```shell
cargo build
```

This outputs an executable.

- Ignored test files: TODO

## Tooling
TODO

### Project creation
TODO

### Package management
TODO

### Testing & linting
TODO

## Hello world
```rust
fn main() {
  println!("Hello, world!");
}
```

## Basics
- Do use semicolons for statements (not for expressions)
- Chars can be denoted using ``` '' ```
- Strings can be denoted using ``` "" ```
- Underscores (``` _ ```) can be used as placeholders for unused values (TODO: ?)

- Default main file: ```main.rs``` (executable projects) or ```lib.rs``` (libraries)
- ```main``` function is called on execution

- Do use ```snake case``` (```snake_case```)

### Comments
```rust
// Single line

// Multi
// line

/* TODO **/
```

### Variables
```rust
// Immutable binding with type
let variable_name: u32 = 0;
// TODO: Multi-declaration

// Mutable binding with type
let mut variable_name: u32;
// TODO: Multi-declaration

// Mutable binding with type and initialization
let mut variable_name: u32 = 0;
// TODO: Multi-declaration

// Types can be inferred
let variable_name = 0;
// TODO: Multi-declaration

let mut variable_name = 0;
// TODO: Multi-declaration

// Constants
const CONSTANT_NAME: u32 = 0
```

### Data types
Rust is statically typed.

#### Primitives (scalar types)
- Boolean: ```bool```
- Integer (```i```: signed, ```u```: unsigned):
  - 8-bit: ```i8```/```u8```
  - 16-bit: ```i16```/```u16```
  - 32-bit: ```i32```/```u32```
  - 64-bit: ```i64```/```u64```
  - architecture: ```isize```/```usize```
- Floating-point: ```f32``` and ```f64```
- Character: ```char```
- Tuples: ```(<type>, <type>, <type>)``` with ```<type>```

For more information, see [here](https://doc.rust-lang.org/book/second-edition/ch03-02-data-types.html).

#### Strings
TODO

#### Generics
TODO

#### Interfaces
TODO

#### Null
TODO

#### Type checks
TODO

#### Type conversion
Types can be converted using the ```.parse()``` method:

```rust
let name: u32 = "0".parse().expect("Not a number!"); // 'expect()' handles error case
```

### Functions
```rust
// Function declarations
fn function_name(param: u32, param2: u32) -> u32 {
  // Statements go here
  param2 // blocks automatically return final expression --> { param2 } is equivalent to { { param2 } }
}

// Function calls
let returnValue = functionName(0, 0);
```

### Flow control

#### If/else
```rust
// If (simple)
if condition { /* Statements go here */ }


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
In Rust, you can use the ```if/else``` construct in place of ```?:``` ternary operator:

```rust
let value = if condition { conditionAppliesValue } else { conditionDoesNotApplyValue };
```

TODO:
Additionally, any expression can be used in a value assignment (e.g. ```if/else-if/else```, ```match```, or any block that ends on an expression).

#### Switch
Rust does not have the ```switch``` keyword. Instead it has something way cooler: pattern matching

```rust
// Match (used like switch)
match value {
  comparedValue => /* Statement goes here */,
  comparedValue2 => {
    // Statements go here
  },
}

// Match (using patterns)
// TODO
```

#### Loops

##### Forever
```rust
loop {
  // Statements go here
}
```

##### Conditional
```rust
// While-like loop
while condition {
  // Statements go here
}
```

##### Count
```rust
for count in (0..10) {
	// Statements go here
}
```

##### Iterate data
```rust
// Array for-each
for value in arrayName.iter() {
  // Statements go here
}
```

Stop a loop using ```break;```, skip an iteration using ```continue;```.

### Data Structures

#### Tuples
Use arrays.

#### Arrays
Rust's arrays are statically-sized.

```rust
// Declare array
let arrayName = [0, 0, 0, 0];
// TODO: Types, additional declarations

// Access array value
let value = arrayName[index];

// Mutate array value
arrayName[index] = value;

// Get array length
// TODO
```

#### Array slices
TODO

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
```rust
// Declare struct type
struct StructTypeName {
  key: u32,
  key2: u32,
}

// Create new struct
let structName = StructTypeName {
  key1: 0,
  key2: 0,
};

// Anonymous struct type
// TODO

// Access struct value
let value = structName.key2;

// Mutate struct value
structName.key2 = value;
```

#### Maps
TODO

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
TODO

### Memory management
> [Rust’s central feature is ownership.](https://doc.rust-lang.org/stable/book/second-edition/ch04-01-what-is-ownership.html)

Rust has a memory management solution that can be best described as "manual-automatic".

To guarantee memory safety, it introduces a special ownership system.

Here are the basic rules:
> 1. Each value in Rust has a variable that’s called its owner.
> 2. There can only be one owner at a time.  
> 3. When the owner goes out of scope, the value will be dropped.
>
> \- [The Rust Programming Language Book](https://doc.rust-lang.org/stable/book/second-edition/ch04-01-what-is-ownership.html#ownership-rules)

When you pass around values, they are moved to the new variable and thus no longer available in the old one.  
An exception to this are types implementing the ```Copy``` trait (e.g. all primitives). Here the value is copied, when you assign it to a new variable, not moved (you can still access it via the old variable afterwards).

This means that whenever you pass values of types not implementing the ```Copy``` trait to a function, it also has to pass them back, if you still want to use them after the function call (in the original scope).

#### Pointers & references
As constantly passing back and forth values might get very tedious, Rust introduces ```borrowing```:

> [We call having references as function parameters borrowing.](https://doc.rust-lang.org/stable/book/second-edition/ch04-02-references-and-borrowing.html)

References are created using the ```&``` sign. They enable you to refer to a value without taking ownership of it. These are by default immutable.

To mutate data via a reference, you need to declare it mutable using ```&mut```. Note: You can only have one mutable reference to the same piece of data at a time (see [here](https://doc.rust-lang.org/stable/book/second-edition/ch04-02-references-and-borrowing.html#mutable-references)). Additionally, when using mutable references, you can not have immutable references at the same time.

The ```*``` sign can be used to access a reference's value (dereferencing).

TODO: Example code

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
Rust's modules are independent namespaces that can selectively expose a part of their members to the outside world.

Additionally multiple modules can be packaged into a ```crate``` that can be published on [Cargo](http://doc.crates.io/), Rust's package manager.  
A crate itself in that case also is a module.

```rust
// Import modules
use module::sub; // Import member of namespace (also works on Enums)
use module::*; // Import all members of namespace
use super::module; // Import namespace from parent module

// Import external packages (crates)
extern crate crate_name;

// Declare modules
mod moduleName {
  fn member() {}
  mod subModule {}
}

mod moduleName; // Look for module implementation in 'name.rs' & 'name/mod.rs', declare here

// Export: prepend 'pub' keyword
mod moduleName {
  pub fn member() {}
  pub mod subModule {}
}
```

### Concurrency
TODO

## Special features

### Macros
TODO

### Pattern matching
TODO