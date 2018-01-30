# ANSI C
C is a (probably *the*) low-level systems programming language.

- File extension: ```**/*.c```

## Hello World
```c
#include <stdio.h>

int main() {
  printf("Hello, world!\n");
  return 0;
}
```

## Basics
- Do use semicolons
- Chars can be denoted using ``` '' ```
- Strings are denoted using ``` "string" ```

- Naming convention: Do use *camel case* (```mixedCaps```/```MixedCaps```)

### Comments
```c
// Single line

/* Multi
line */
```

### Variables
```c
// Mutable binding, declaration
int variableName;
int variableName, variableName2;

// Mutable binding, declaration with initialization
int variableName = 0;
int variableName = 0, variableName2 = 0;

// Constants
int const constantName = 0;
const int constantName = 0;

// Constants can also be defined using the preprocessor #define
#define CONSTANT_NAME 0
```

### Data types
C is statically typed.

#### Primitives
- Boolean: ```bool``` (using ```#include <stdbool.h>``` in C99)
- Integer (default: signed, prefix with ```unsigned```: unsigned):
  - 8-bit: ```char```/```unsigned char```
  - 16-bit: ```short```/```unsigned short```
  - 16-bit/32-bit: ```int```/```unsigned int```
  - 32-bit: ```long```/```unsigned long```
- Floating-point:
  - 32-bit: ```float```
  - 64-bit (double-precision): ```double```
  - 80-bit: ```long double```
- Void (no value available): ```void```

#### Strings
In C strings are one-dimensional arrays of chars terminated by a *null* character (```\0```).

```c
// Declare & initialize string (manually)
char stringName[4] = {'s', 't', 'r', '\0'};

// Declare & initialize string (using string constant)
char stringName[10] = "str"; // Automatically assigns '\0' to 4th char

// String methods
#include <string.h>

// Copy string
strcpy(stringName, "str2") // Write string constant "str2" to 'stringName'
strcpy(stringName2, stringName) // Copy from 'stringName' to 'stringName2'

// Concatenate
strcat(structName, stringName2) // Concatenate 'stringName2' onto the end of 'stringName'

// Get string length
int length = strlen(stringName);
```

#### Interfaces
ANSI C does not have Interfaces

#### Null
- ```NULL```

#### Type checks
TODO

#### Type conversion
```c
// Type casting
double variableName = (double) intVariableName;

// Parse string as int
#include <stdlib.h>
int variableName = atoi(stringVariableName)
```

### Functions
```c
// Function declarations
int functionName(int param, int param2) {
  // Statements go here
  return param2;
}

// Function calls
int returnValue = functionName(0, 0);
```

### Flow control

#### If/else
```c
// If shorthand
if (condition) // Statement goes here

// If/else-if/else
if (condition) {
  // Statements go here
} else if (condition2) {
  // Statements go here
} else {
  // Statements go here
}
```

#### Conditional expression
C has the ```?:``` ternary operator.

```c
int value = condition ? conditionAppliesValue : conditionDoesNotApplyValue;
```

#### Switch
```c
switch (value) {
  case comparedValue:
    // Statements go here
    break;

  default:
    // Statements go here
}
```

#### Loops

##### Forever
```c
while (1) {
  // Statements go here
}
```

##### Conditional
```c
// While shorthand
while (condition) // Statement goes here

// While loop
while (condition) {
  // Statements go here
}
```

##### Count
```c
// For loop (variable declaration in for loop from C99 owards)
for (int count = 0; count < 10; count++) {
  // Statements go here
}
```

### Data Structures

#### Tuples
Use structs.

#### Arrays
```c
// Declare array
int arrayName[10];

// Declare & initialize array
int arrayName[3] = {0, 1, 2};
int arrayName[] = {0, 1, 2};

// Access array value
int value = arrayName[index];

// Mutate array value
arrayName[index] = value;
```

#### Array slices
C does not natively have array slices.

#### Generic Objects
Use structs.

#### Structs
```c
// Declare struct type
struct StructTypeName {
  int key;
  int key2;
};

// Create new struct variable
struct StructTypeName structName;

// Create & initialize new struct variable
struct StructTypeName structName = { 0, 0 };

// Anonymous struct type
struct {
  int key;
  int key2;
} structName = { 0, 0 };

// Access struct value (member)
int value = structName.key2;

// Mutate struct value (member)
structName.key2 = value;

// Pointers to structs
// Create & initialize a pointer to a struct variable
struct StructTypeName *structPointerName = &structName;

// Access struct value (member) from pointer
int value = structPointerName->key;

// Mutate struct value (member) from pointer
structPointerName->key = value;
```

#### Maps
Use structs.

### Classes/methods
ANSI C is not an object oriented programming language. Thus it does not have a classes.

### Memory management
TODO

#### Pointers & references
TODO

### Modules
C has header files (```**/*.h```) that contain shared C function declarations and macros definitions.  
Generally two types of header files are discerned: Those the programmer writes himself, and those that ship with the compiler.
Both can be imported using their respective version of the ```#include``` preprocessing directive.

```c
// Import system header file (ships with compiler)
#include <file.h>

// Import user header file (searches the current file's directory)
#include "file.h"
```

### Concurrency
TODO

## Special features

### Ternaries
See "Flow control" > "Conditional expression"

### Macros
TODO

### Preprocessing directives
TODO
