# JavaScript Essentials
Brendan Eich created JavaScript, a scripting language\
*A scripting language is a type of programming language used to give instructions to a computer without compiling the code first.*\
*JavaScript still runs without compilation in browsers*
JavaScript first allocates memory for variables and functions (hoisting), then executes code line-by-line in a single-threaded, top-down manner.\
Assembly lang are bottom-up mean, solving sub prblms and then bigger prblm solving

It is a dynamically typed language, meaning that a variable's data type is determined at runtime. You do not have to declare the data type of a variable before using it. \
`console.log (12,13,14..)`  can print multiple values\
`===` compares datatype and value\
charAt(index) function of the JavaScript string finds a char element at the supplied index. 


Debugging happens during execution/run time, not during compilation.\
JavaScript follows camelCase because it inherited naming conventions from Java, it improves readability for multi-word identifiers, and it keeps consistency with DOM APIs.

---

## Advantages 
  - Client + Server Side: JavaScript runs in both browser (frontend) and server (via Node.js).
  - Easy to Learn: Simple syntax and beginner-friendly.
  - Fast Execution: Runs directly in the browser, no compilation needed.
  - Enhanced Interactivity: Enables dynamic content, animations, form validation, etc.
  - Wide Ecosystem: Huge collection of frameworks (React, Vue, Angular) and libraries.
  - Platform Independent: Works on all major browsers and devices.
  - Supports OOP & Functional Programming: Flexible and powerful for various programming styles.

## Errors
| Error Type    | Happens When?           | Example                           | Error Message Example           |
| ------------- | ----------------------- | --------------------------------- | ------------------------------- |
| Syntax Error  | Code violates JS syntax | Missing `)` or `{`                | `SyntaxError: Unexpected token` |
| Runtime Error | Code tries illegal ops  | Using undefined variable/function | `ReferenceError`, `TypeError`   |
| Logical Error | Logic is incorrect      | Output is wrong but no crash      | No error, just wrong output     |

## External Javascript

Best Practices:\
Place <script> before the closing </body> tag so the HTML loads first, improving performance.

If you need to keep scripts in <head>, use defer:
`<script src="script.js" defer></script>` \
Advantages:
  - It allows web designers and developers to collaborate on HTML and javascript files.
  - We can reuse the code.
  - Code readability is simple in external javascript.

## Scope 
It lets us know at a given part of code, what are variables and functions we can or cannot access.\
There are three types of scopes in JS:\
  - Global Scope
  - Local or Function Scope
  - Block Scope

## Scope Chain
It's the process JavaScript uses to look up variables when they're used in nested functions.\

i.e. When a variable is used inside a function, JavaScript:\
  - Looks for it inside that function (local scope).
  - If not found, looks one level up (parent scope).
  - Keeps going up the chain until it reaches the global scope.
  - If it’s still not found, it throws a ReferenceError.


## Implicit Type
Coercion is when JavaScript automatically converts one data type to another during operations like comparisons or arithmetic — without you asking it to.

## 🧾 Variable Declarations (Keyword for varibles dec)
- Use **const** for variables that should not be reassigned after their initial value is set. Block + function Scope
- Use **let** for variables whose values need to be reassigned within a block scope.
- **var** is generally discouraged in modern JavaScript development due to its function-scoping and hoisting behavior which can lead to unexpected issues, favoring let and const for better control over variable scope and mutability. var is attached to the **global window object** when declared globally.
  `Function scope: var can leak outside block, accessible in parent function`
    Main issues of var:
    - Doesnot prevent redeclaration within the same scope.
    - When var is declared in the global scope (outside of any function), it becomes a property of the global object (e.g., window in browsers).
    - Function Scope, Not Block Scope:


We can do `a=9` without mentioning the data type, and it'll NOT throw error if we do this outside of strict mode( JavaScript will implicitly create a global variable a.) , Bt in strcit mode, it'l throw an error\



---
  
## Temporal dead zone
When you declare a variable using let or const, it is hoisted (moved to the top of the scope), but not initialized.\
Until the code execution reaches the declaration line, that variable is in the "temporal dead zone", meaning you cannot access it — doing so will throw a ReferenceError.


## 🔁 Hoisting
- **Hoisting is JavaScript's default behavior of moving declarations (not assignments) to the top of the current scope (global or function scope).**
  - *This means you can use variables (only var) and call functions before they are formally declared in your code.*
 ```javascript
console.log(a); // undefined
var a = 10;
```

becomes
 ```javascript
var a;        // Declaration is hoisted to the top
//CODE
console.log(a); // undefined
a = 10;       // Initialization stays in place

```

All var, let, const are hosted but only accessible for var
- You can reference variables/functions before they are declared, but:
  - `var` gives `undefined`
  - `let`/`const` give `ReferenceError`

Function declarations (function sayHello) are hoisted with their body.\
Variables declared with var are hoisted as undefined (without assignment).\ 

  - ---
## 🗃️  JavaScript Data Types

### 🔹 Primitive Types
- Immutable
- Assigned **by value**
- Types: `String`, `Number`, `BigInt`, `Boolean`, `Undefined`, `Null`, `Symbol(ES6 version)`

*Type of null is object: It’s a bug because in early JavaScript, values were stored with type tags in binary, and null was represented as all zeros (0000), the same tag used for objects, so typeof null incorrectly returns "object".*

We can mutability using a wrapper object: i..e let x = { y:6} then x.y=7 

### 🔸 Reference Types [], {}, ()
- Mutable: changes through one variable reflect in others pointing to the same object.
- Assigned **by reference**
- Types: `Object`, `Array`, `Function`

### ⚖️ Key Differences

| Feature     | Primitive     | Reference     |
|-------------|---------------|----------------|
| Mutability  | Immutable     | Mutable        |
| Assignment  | By value      | By reference   |
| Comparison  | Value-based   | Reference-based |


Why, Objects are mutable? 
1. Efficiency & Performance (Memory Optimization)
2. Objects Are Meant to Be Updated

How to copy ref values? **Using Spread operator [...]**
```js
var a = [12, 13];
var b = a;

b[0] = 99;    // modifying array contents
console.log(a); // [99, 13] — changes reflect in 'a'
```

but when we do,
```js
var a = [12, 13];
var b = [...a]; // creates a shallow copy

b[0] = 99; 
console.log(a); // [12, 13] — original unchanged
```

**It copies!!** 

---

## Functions

Declared by `function X() {}`\
In JavaScript, functions are first-class citizens — this means: Functions can be treated like any other variable.

**JavaScript functions are objects — and objects are assigned by reference, not by value.**
thus when we do
```js
const X = obj.Y;
```
then Both obj.Y and X now point to the same function object in memory.

The values we **send** are arguments\
While the values that're in function () are parameters\

**Call-Back Function:** A function passed into another function\
**Anonymous Function:** Without any name,  eg:
`function () { ... } when passed as an Argument, callback`
`() => { ... }`

**First-Class Function** Func that can be treated as a variable or a value \
**Higher Order Function** Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions.\

HOF = function that uses another function.\
Callback = the function being used.

**Generator Function**: Func that can pause and resume execution.
    - Defined using function* syntax.
    - Uses the yield keyword to pause.
    - Returns an iterator object when called.

**Pure Function:** A pure function is one that:
                - Depends only on its input → Output is determined only by the arguments passed.
                - Has no side effects → It doesn’t change anything outside itself (like global variables, DOM, console, etc.).

*Impure fnctions are opposite of it*

```js
//PURE FUNCTIONS
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 5
console.log(add(2, 3)); // always 5 (same input → same output)

```

```js
//IMPURE FUNCTIONS
let counter = 0;

function increment() {
  counter++;
  return counter;
}

console.log(increment()); // 1
console.log(increment()); // 2 (same input, different output)
```

---

## New Keyword

Always creates a blank object for constructor function which is getting called, AFTER the new keyword


### ✅ Truthy and ❌ Falsy in JavaScript
7 Falsy values:
```js
null
undefined
false
NaN, To check if a value is NaN, we use the isNaN() function,
0
-0
0n        // BigInt zero
""        // Empty string
documnet.all
```
Everything else: Truthy\

0n: BigInt in JavaScript is a special numeric type that lets you store and work with integers larger than Number.MAX_SAFE_INTEGER (2⁵³ - 1) without losing precision.\
How to create? `const big2 = BigInt("X");` or `const big = Xn;`



---
## Pop-Up functions

.alert\
.error\
.warn\
.prompt\
.confirm

---
## JavaScript Array Methods
Arrays are Objects i.e.
```js
let array = {
  0:x,
  1:y,
  2:z
}
i.e. array=[x,y,z]
```

thu we can even store negative index i.e.
`array[-a]=b` i.e.array=[x,y,z,-a:b]\

Array.isArray([]) TRUE\
Array.isArray({}) FALSE\


### Mutating Methods (modify the original array)

| Method         | Description                                      |
|----------------|--------------------------------------------------|
|**`push()`**    | Adds element(s) to the **end** of the array      |
| **`pop()`**    | Removes the **last** element                     |
| **`shift()`**  | Removes the **first** element                    |
| **`unshift()`**| Adds element(s) to the **beginning**             |
| **`splice()`** | Adds/removes/replaces elements at a given index  |
| `sort()`       | Sorts array **in place**                         |
| `reverse()`    | Reverses the array **in place**                  |
| `fill()`       | Fills elements with a static value               |
| `copyWithin()` | Copies part of the array within itself           |

`array.splice(start, deleteCount, item1, item2, ...)`
  - start → Index to start changing the array.
  - deleteCount → Number of elements to remove.
  - item1, item2, ... → Elements to insert at start index.

`map returns a new array, forEach returns undefined.`

### 🔸 Non-Mutating Methods (return new array or value)

| Method           | Description                                     |
|------------------|-------------------------------------------------|
| `concat()`       | Merges two or more arrays                       |
| `slice()`        | Returns a shallow copy of a portion             |
| `map()`          | Transforms elements into a new array            |
| **`filter()`**   | Filters elements based on a condition           |
| **`reduce()`**   | Reduces array to a single value                 |
| `reduceRight()`  | Like reduce, but right-to-left                  |
| `find()`         | Finds the **first** matching element            |
| `findIndex()`    | Finds the **index** of the first match          |
| `includes()`     | Checks if a value exists in the array           |
| `indexOf()`      | Gets the index of a value                       |
| `lastIndexOf()`  | Gets the last index of a value                  |
| `join()`         | Joins elements into a string                    |
| `toString()`     | Converts array to string                        |
| `every()`        | Returns true if **all** elements match condition|
| `some()`         | Returns true if **any** element matches         |
| `flat()`         | Flattens nested arrays                          |
| `flatMap()`      | `map()` + `flat()`                              |
| `entries()`      | Returns iterator of `[index, value]` pairs      |
| `keys()`         | Returns iterator of indexes                     |
| `values()`       | Returns iterator of values                      |
| `from()`         | Converts iterable or array-like to array        |
| `isArray()`      | Checks if a value is an array                   |


`array.reduce(callback(accumulator, currentValue, index, array), initialValue)`
  - accumulator → Holds the accumulated result.
  - currentValue → The current array element.
  - initialValue → (Optional) Starting value for the accumulator.

### 🆕 ES6+ Additions

- `Array.from()` – Creates array from iterable
- `Array.of()` – Creates array from given arguments
- `flat()` – Flattens nested arrays
- `flatMap()` – Maps and flattens in one step

```js
const arr = [1, [2, [3, [4, [5]]]]];

console.log(arr.flat());        // [1, 2, [3, [4, [5]]]]   → default depth = 1
console.log(arr.flat(2));       // [1, 2, 3, [4, [5]]]     → depth = 2
console.log(arr.flat(Infinity)); // [1, 2, 3, 4, 5]        → fully flattened
```

---

## JavaScript String Methods

| Function        | What it does                      | Example                          |
| --------------- | --------------------------------- | -------------------------------- |
| `length`        | Gets the length                   | `"hello".length` → `5`           |
| `charAt()`      | Gets a character at a position    | `"hello".charAt(1)` → `"e"`      |
| `indexOf()`     | Finds first position of text      | `"hello".indexOf("l")` → `2`     |
| `lastIndexOf()` | Finds last position of text       | `"hello".lastIndexOf("l")` → `3` |
| `includes()`    | Checks if text exists             | `"hello".includes("he")`         |
| `startsWith()`  | Checks beginning of string        | `"hello".startsWith("he")`       |
| `endsWith()`    | Checks end of string              | `"hello".endsWith("lo")`         |
| `toUpperCase()` | Makes uppercase                   | `"hi".toUpperCase()`             |
| `toLowerCase()` | Makes lowercase                   | `"HI".toLowerCase()`             |
| `trim()`        | Removes spaces at start/end       | `" hi ".trim()`                  |
| `slice()`       | Extracts part of string           | `"hello".slice(1,4)` → `"ell"`   |
| `substring()`   | Similar to slice but no negatives | `"hello".substring(1,4)`         |
| `substr()`      | Same as slice by deprecated       |
| `replace()`     | Replaces first match              | `"hi hi".replace("hi","bye")`    |
| `replaceAll()`  | Replaces all matches              | `"hi hi".replaceAll("hi","bye")` |
| **`split()`**   | **Turns string into array**       | `"a,b,c".split(",")`             |
| `repeat()`      | Repeats string                    | `"ha".repeat(3)` → `"hahaha"`    |


`string.split(separator, limit)`
  - separator → What to split on (string or regex).
  - limit → Optional; maximum number of splits.



## Object
It Holds information of a person/thing in form of `key:value` pair\
*Key* can be a a property\
when value of a key becomes a function, the *key* becomes a method i.e. `key:function(){..}` here key is a method

```js
const obj = {
  name: "John",
  age: 21
};
```
**We can copy Object, using {...a}**

to change value, obj.name=xyz\
to access value, obj.name obj[name]\
  &nbsp; &nbsp; in for...in loop, we take a variable which iterates over keys, thus we need to do `obj[name]`
to delete key:value, delete obj.key\

### ProtoType in Object

Every created object gets a property called as Prototype automatically. `[[Prototoype]]`\
The prototype is itself an object, so the prototype will have its own prototype, making what's called a prototype chain. The chain ends when we reach a prototype that has null for its own prototype.

Usage: **It contains many helper properties and methods** (eg .length)\
These properties and methods points to same properties and methods and doesn't create a new memory for storing these. Thus changes made in one will affect in all objects that is using these prop and methods

It's a mechanism by which JS objects inherit features from one another.\

We can access this prototype object using: obj.__proto__
here, this'll be referencing to that prtotype object and thsu we can make changes in that prototype object as well.

We can directly access the Prototype object as `object.prototype`

### ProtoTypal Inheritance

Inheritance: Passing features of Parents to Children. In JavaScript, inheritance is performed through the prototype chain instead of Class chain. \

```js
let animal = {
  eats: true
};

let dog = {
  barks: true
};

// Set prototype manually
dog.__proto__ = animal;

// OR In modern way we use:
Object.setPrototypeOf(dog, animal);

console.log(dog.barks); // true (own property)
console.log(dog.eats);  // true (inherited from animal via __proto__)
```
`Note: __proto__ works, but it’s considered legacy (not recommended for direct use).`




## Recursion
Recursion is a technique to iterate over an operation by having a function call itself repeatedly until it arrives at a result.


const { getX } = obj; is same as const getX = obj.getX;
