# JavaScript Essentials

`console.log (12,13,14..)`  can print multiple values\
`===` compares datatype and value

---


## 🧾 Variable Declarations
- Use **const** for variables that should not be reassigned after their initial value is set. 
- Use **let** for variables whose values need to be reassigned within a block scope.
- **var** is generally discouraged in modern JavaScript development due to its function-scoping and hoisting behavior which can lead to unexpected issues, favoring let and const for better control over variable scope and mutability. var is attached to the **global window object** when declared globally.
  `Function scope: var can leak outside block, accessible in parent function`
---

## 🔁 Hoisting
- **Hoisting is JavaScript's default behavior of moving declarations (not assignments) to the top of the current scope (global or function scope).**
  - *This means you can use variables and call functions before they are formally declared in your code.*
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

- You can reference variables/functions before they are declared, but:
  - `var` gives `undefined`
  - `let`/`const` give `ReferenceError`
  - ---
## 🗃️  JavaScript Data Types (Quick Summary)

### 🔹 Primitive Types
- Immutable
- Assigned **by value**
- Types: `String`, `Number`, `BigInt`, `Boolean`, `Undefined`, `Null`, `Symbol`

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
---

## Functions

Declared by `function X() {}`

The values we **send** are arguments
While the values that're in function () are parameters

---


### ✅ Truthy and ❌ Falsy in JavaScript
7 Falsy values:
```js
false
0
-0
0n        // BigInt zero
""        // Empty string
null
undefined
NaN
```
Everything else: Truthy

---
## Pop-Up functions

.alert\
.error\
.warn\
.prompt\
.confirm

---
## JavaScript Array Methods


### Mutating Methods (modify the original array)

| Method         | Description                                      |
|----------------|--------------------------------------------------|
|**`push()`**    | Adds element(s) to the **end** of the array      |
| **`pop()`**    | Removes the **last** element                     |
| **`shift()`**  | Removes the **first** element                    |
| **`unshift()`**| Adds element(s) to the **beginning**             |
| **`splice()`** | Adds/removes/replaces elements at a given index |
| `sort()`       | Sorts array **in place**                         |
| `reverse()`    | Reverses the array **in place**                  |
| `fill()`       | Fills elements with a static value               |
| `copyWithin()` | Copies part of the array within itself           |



### 🔸 Non-Mutating Methods (return new array or value)

| Method          | Description                                      |
|------------------|--------------------------------------------------|
| `concat()`       | Merges two or more arrays                       |
| `slice()`        | Returns a shallow copy of a portion             |
| `map()`          | Transforms elements into a new array            |
| `filter()`       | Filters elements based on a condition           |
| `reduce()`       | Reduces array to a single value                 |
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



### 🆕 ES6+ Additions

- `Array.from()` – Creates array from iterable
- `Array.of()` – Creates array from given arguments
- `flat()` – Flattens nested arrays
- `flatMap()` – Maps and flattens in one step

---


## Object
It Holds information of a person/thing in form of `key:value` pair
*Key* can be a a property
when value of a key becomes a function, the *key* becomes a method i.e. `key:function(){..}` here key is a method

