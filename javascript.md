# JavaScript (ECMAscript 6)
Java script is a dynamically typed, garbage collected interpreter language predominantly found in the browser and server-side using [node.js](https://nodejs.org).

- Abbreviations: JS, ES6
- File extension: ```**/*.{js,es6,jsx}```
- Default main file (per directory): ```index.js```

- Project configuration files:
  - [```package.json```](https://docs.npmjs.com/files/package.json)
  - ```yarn.lock``` (when using [Yarn](https://yarnpkg.com/en/) as your package manager)

## Get Started
This guide focuses on setting up and working with *node.js*

### Setup
Just [download](https://nodejs.org/en/download/) and install node

### REPL
```shell
node
```

### Execute scripts
```shell
node index.js
```

### Compile
Although it often times is advisable for performance reasons, you do not necessarily have to compile/transpile your source code, if you are not targeting any older platforms that do not yet support all of the ES6 features (see [caniuse.com](http://caniuse.com/#cats=JS) for Brower compatibility and [node.green](http://node.green/) for ES6 support in node.js).

If you decide to include a build step into your development pipeline (which you totally should, especially if you are targeting browsers), popular choices are [Webpack](https://webpack.js.org/) + [Babel](https://babeljs.io/).  
If you want to get even fancier, you can try out something like [TypeScript](http://www.typescriptlang.org/), a JavaScript superset that adds static type checking on top of ES6/7, or any of the other countless compile-to JS solutions (e.g. [Elm](http://elm-lang.org/), or even one for a more traditional language like [Haskell](https://wiki.haskell.org/The_JavaScript_Problem#Haskell_-.3E_JS)).

## Tooling
When working with node.js, you get to use node's awesome package manager [NPM](https://www.npmjs.com/) or any of its 3rd party alternatives. Especially [Yarn](https://yarnpkg.com/en/) is a very popular and sophisticated choice here that has many advantages over just using NPM.

### Project creation
New projects can easily be initialized using the ```npm init```/```yarn init``` command. Just follow the onscreen instructions and a ```package.json``` file describing our project will be created.

### Package management
When checking out a project, you can install previously added dependencies using
- ```npm install```
- or ```yarn```

You can add new packages to your project using
- ```npm install --save <package> <package2> <packageN>```
- or ```yarn add <package> <package2> <packageN>```

Installed packages will be saved in the ```node_modules``` directory which should **not** be included into version control, and will be marked as a dependency in your ```package.json``` (which you absolutely have to include into version control).

You can also add development dependencies that are exclusively used in your development pipeline (e.g. testing frameworks or build tools) and are not required for the final program to run:
- ```npm install --save-dev <package> <package2> <packageN>```
- ```yarn add --dev <package> <package2> <packageN>```

Installed packages can be removed using
- ```npm uninstall --save <package> <package2> <packageN>```
- or ```yarn remove <package> <package2> <packageN>```

### Testing & Linting
A variety of different unit testing & linting solutions for JS exist.

Popular choices for testing include
- [Jasmine](https://jasmine.github.io/)
- [Jest](https://facebook.github.io/jest/)
- [Karma](https://karma-runner.github.io/)
- [Mocha](http://mochajs.org/)
- and many more

For linting [ESLint](http://eslint.org/) generally is advisable.

## Hello World
```javascript
console.log('Hello, world!');
```

## Basics
- Do use semicolons (technically they are optional in most places - huge debates about whether you should use them here can be had)
- Strings can be denoted using ``` '<string>' ```,  ``` "<tring>" ``` or ``` `<string>` ```
- Value equality (w/o type coercion) is checked with ```===```

- Naming convention: Do use ```camel case``` (```mixedCaps```/```MixedCaps```)

### Comments
```javascript
// Single line

/* Multi
line */

/** JSDoc single line */

/**
 * JSDoc multi line
 */
```

[JSDoc](http://usejsdoc.org/) is a tool for generating automatic documentation for your code. Its annotation syntax is also widely used to display short descriptions for e.g. function name autocompletion in many editors.

### Variables
```javascript
// ES5 variable (do not use in ES6!)
var variableName = 0;

// Mutable binding (block-scoped)
let variableName;

// Mutable binding (block-scoped) with initialization
let variableName = 0;

// Constants/immutable binding (block-scoped)
const variableName = 0;
```

### Data types
JavaScript is dynamically typed. You cannot declare static types (although 3rd party static type checking solutions for JavaScript exist: e.g. [TypeScript](http://www.typescriptlang.org/), [flow](https://flow.org/)).

#### Primitives
- Boolean
- Null
- Undefined
- Number
- String
- Symbol (new in ES6)

For more information, take a look at the [Mozilla JavaScript reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures).

#### Strings
JavaScript's strings are treated like primitives.

#### Interfaces
JavaScript does not have interfaces.

#### Null
Variables declared without initialization have a value of ```undefined```.

The following null types exist:
- ```undefined``` - name not defined/holds no value
- ```null```
- ```NaN``` (```NaN !== NaN```!) - value is not a number

#### Type checks
Types can be checked at runtime:

```javascript
const variableName = 0;
class ClassName {}

console.log(typeof variableName === 'number'); // true
console.log((new ClassName()) instanceof ClassName); // true
```

For more information, take a look at the [Mozilla JavaScript reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof).

#### Type conversion
JavaScript implicitly coerces types as needed.  
Explicit conversion can be achieved as follows:

```javascript
// Using parse functions
console.log(parseInt('0')); // 0
console.log(parseFloat('0')); // 0

// Explicit type coercion
console.log(Boolean(0)); // false
console.log(Number('0')); // 0
console.log(String(0)); // '0'
// ...

// Using implicit coercion
// Example: boolean
console.log(!0); // true
console.log(!!0); // false
```

### Functions
The following functions all take two arguments and return the value of the second one.

```javascript
// Arrow function (new in ES6, do use for almost everything), return shorthand
const functionName = (param, param2) => param2;

// Arrow function, w/ function curly function body
const functionName = (param, param2) => {
  // Additional statements go here
  return param2;
}

// ES5 function declaration (do only use in ES6 if 'this' must be used)
function functionName(param, param2) {
  // Additional statements go here
  return param2;
}

// ES5 anonymous function assignment (do only use in ES6 if 'this' must be used)
const functionName = function (param, param2) {
  // Additional statements go here
  return param2;
}

// Rest parameters (take an indefinite amount of arguments as an array)
const functionName = (...args) => args[1];

// Parameters with default value
const functionName = (param = 0, param2) => param2;

// Function calls (all succeed on all declared functions)
const returnValue = functionName(); // returnValue is undefined
const returnValue = functionName(0); // returnValue is undefined
const returnValue = functionName(0, 0); // returnValue is 0
const returnValue = functionName(0, 0, 0/*, ...*/); // returnValue is 0
```

### Flow control

#### If/else
```javascript
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
JavaScript has the ```?:``` ternary operator.

```javascript
const value = condition ? conditionAppliesValue : conditionDoesNotApplyValue;
```

#### Switch
```javascript
switch (value) {
  case comparedValue:
    // Statements go here
    break;

  // Use curly braces when declaring block-scoped variables in a case
  case comparedValue2: {
    // Statements go here
    break;
  }

  default:
    // Statements go here
}
```

#### Loops

##### Forever
```javascript
while (true) {
  // Statements go here
}
```

##### Conditional
```javascript
// While shorthand
while (condition) // Statement goes here

// While loop
while (condition) {
  // Statements go here
}
```

##### Count
```javascript
// For loop
for (let count = 0; count < 10; count++) {
  // Statements go here
}
```

##### Iterate data
```javascript
// For-in loop (objects)
for (let key in objectName) {
  if (Object.prototype.hasOwnProperty(objectName, key)) {
    const value = objectName[key];
    // Statements go here
  }
}

// Array for-each
arrayName.forEach((currentValue, index, array) => {
  // Statements go here
});

// Iterate objects ES6-style
Object.keys(objectName).forEach((key) => {
  const value = objectName[key];
  // Statements go here
});
```

Stop a ```while``` or ```for``` loop using ```break;```, skip an iteration using ```continue;```.

### Data Structures

#### Tuples
Use arrays.

#### Arrays
JavaScript's array are always dynamically-sized. Internally they are implemented as linked lists.

```javascript
// Declare array
const arrayName = [];
const arrayName = [0, 1, 2];

// Access array value
const value = arrayName[index];

// Mutate array value
arrayName[index] = value;

// Get array length
const length = arrayName.length; // Important: dynamically computed (reading it is O(n))!

// Array methods (examples return new arrays with identical data)
const arrayName2 = arrayName.filter((currentValue, index, array) => true);
const arrayName3 = arrayName.map((currentValue, index, array) => currentValue);
// ... (see https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
```

#### Array slices
JavaScript does not natively have array slices.

#### Generic Objects
```javascript
// Create new object
const objectName = {};
const objectName = {
  key: value,
  key2: value2,
};

// Access object value
const value = objectName.key2;
const value = objectName['key2'];

// Mutate object value
objectName.key2 = value;
objectName['key2'] = value;

// Delete object property
delete objectName.key2;
```

#### Structs
Use classes.

#### Maps
Use generic objects.

### Classes/methods
```javascript
// Declare class
class ParentClassName {}

class ClassName extends ParentClassName {
  // ES7 static attribute
  static staticAttributeName = 0;

  // ES7 static method
  static staticMethodName(param, param2) {
    return param2;
  }

  // ES7 instance attribute
  attributeName = 0;

  // Constructor
  constructor(param2, param2) {
    // Mutate instance attribute
    this.attributeName = param2;
  }

  // Instance method
  methodName(param, param2) {
    // Access instance attribute
    return this.attributeName
      + param2;
  }

  // Getter method
  get virtualAttributeName() {
    return this.attributeName;
  }

  // Setter method
  set virtualAttributeName(value) {
    this.attributeName = value;
  }
}

// Access static attribute
const value = ClassName.staticAttributeName;

// Mutate static attribute
ClassName.staticAttributeName = 1;

// Call static method
ClassName.staticMethodName(0, 0); // returns 0

// Create class instance
const instanceName = new ClassName(0, 0);

// Access instance attribute
const value = instanceName.attributeName;
const value = instanceName.virtualAttributeName; // get value of 'attributeName' via getter method

// Mutate instance attribute
instanceName.attributeName = 1;
instanceName.virtualAttributeName = 1; // set value of 'attributeName' via setter method

// Call instance method
instanceName.methodName(0, 1) // returns 2
```

### Memory management
JavaScript is garbage collected. Manual memory management is neither required nor possible.

#### Pointers & references
All JavaScript objects (that includes Arrays) are passed around as references.  
This happens automatically and requires no explicit pointer/reference notation.

### Modules
Each source file is treated as an independent module with its respective imports & exports.

You can put a collection of files into a package that then usually is published on [NPM](https://www.npmjs.com/), Node.js's package manager. Such a package has a ```main``` (specified in the [```package.json```](https://docs.npmjs.com/files/package.json) file in the package root) module that poses as an entry point and often is the only part of the package the package consumer explicitly imports.

Local modules are imported using their relative path (e.g. ```'./module'```, ```'../module'```).
Modules from NPM are imported using a package name (e.g. ```'module'```, ```'module/sub'```).

```javascript
// Import
import defaultExport from 'module';
import { namedExport, namedExport as importName } from 'module';
import defaultExport, { namedExport } from 'module';
import * as module from 'module';

// Declare module: Just add exports to a file and it will be usable as a module

// Export
export default defaultExport;
export { namedExport, namedExport as exportName };
export const namedExport = 0;

// Reexport
export * from 'module';
export { namedExport, namedExport as exportName, default as exportName } from 'module';
```

### Concurrency
JavaScript programs run in a single event loop. (Manual multi-processing is possible in node.js.)

TODO: Asynchronous concept

### Async/await
Before ```async/await``` (and Promises) JavaScript suffered from something called the ["callback hell"](http://callbackhell.com/) (big time!).  
Now you can easily execute asynchronous functions one after another - just as if you were writing (blocking) synchronous code.

Note that ```async/await``` did not make it into the official ES6 spec. It is however part of ES7.

```javascript
// 'await' can only be used inside of 'async' functions
const asyncFunctionName = async () => {
    const resultA = await firstAsyncCall();
    const resultB = await secondAsyncCall(resultA);
    return doSomethingWith(resultB);
};

// 'async' functions return promises (https://www.promisejs.org/)
asyncFunctionName().then((value) => {
  // Statements go here
})
```

For more information, see [this lovely in-depth guide](https://github.com/yortus/asyncawait) and the [```async/await``` draft](https://tc39.github.io/ecmascript-asyncawait/).

## Special features

### Ternaries
See "Flow control" > "Conditional expression"

### Template literals
ES6 has support for advanced string evaluation using template literals.

To define a template literal you have to
- denote you string using ``` `<string>` ``` (with ```<string>``` being your template literal)
- wrap expressions that should be evaluated like this: ```${<expression>}``` (with ```<expression>``` being your expression)

```javascript
const variableName = 0;

console.log(`This is a template literal.
  The variable 'variableName' has a value of ${variableName}.
  If we add 1, we have ${variableName + 1}.
`);

/*
The above outputs:

This is a template literal.
  The variable 'variableName' has a value of 0.
  If we add 1, we have 1.
*/
```

### Destructuring assignments
JavaScript enables you to use destructuring patterns in variable assigments and function parameters.
For more information, take a look at the [Mozilla JavaScript reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).

#### Arrays
```javascript
const arrayName = [0, 1];
const [value, value2] = arrayName;

console.log(value); // 0
console.log(value2); // 1

// Default values (+ skip first two values)
const [,, value03 = 4] = arrayName;

console.log(value01); // 0
console.log(value02); // 1
console.log(value3); // 4

// Example: swap
let a = 0;
let b = 1;
[a, b] = [b, a];

console.log(a); // 1
console.log(b); // 0
```

#### Objects
```javascript
const objectName = { key: 'value', key2: 'value2', key3: 'value3' };
const { key, key3 } = objectName;

console.log(key); // 'value'
console.log(key3); // 'value3'

// Default values
const { key4 = 1 } = objectName;

console.log(key4); // 1

// Rename
const { key3: variableName } = objectName;

console.log(variableName); // 'value3'

// Example: function parameter
const functionName = ({ color }) => color;

console.log(functionName({  background: '#000', color: '#fff' })); // '#fff'
```

### Rest/spread
In ES6 you can "spread" and "rest" arrays and objects.

#### Arrays
For rest parameter usage see "Functions".

```javascript
// Array spread
const arrayName = [1, 2, 3];
const arrayName2 = [0, ...arrayName, 4, 5];

console.log(arrayName2); // [0, 1, 2, 3, 4, 5]

functionName(...arrayName); // Equals functionName(0, 1, 2, 3);

// Array rest
const [value, value2, ...arrayName3] = arrayName2;

console.log(value); // 0
console.log(value2); // 1
console.log(arrayName3); // [2, 3, 4, 5]
```

#### Objects
Please note that the object rest/spread feature is still a [draft](https://github.com/tc39/proposal-object-rest-spread) and is not included in the official ES6 spec.  
Many transpilers do however already support it today.

```javascript
// Object spread
const objectName = { key: 'value', key3: 'value3' };
const objectName2 = { ...objectName, key2: 'value2' };

console.log(objectName2); // { key: 'value', key3: 'value3', key2: 'value2' }

// Object rest
const { key3, ...objectName3 } = objectName2;

console.log(key3); // 'value3'
console.log(objectName3); // { key: 'value', key2: 'value2' };
```
