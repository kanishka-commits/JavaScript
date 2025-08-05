# JavaScript Essentials

## 🧾 Variable Declarations
- Use **const** for variables that should not be reassigned after their initial value is set. 
- Use **let** for variables whose values need to be reassigned within a block scope.
- **var** is generally discouraged in modern JavaScript development due to its function-scoping and hoisting behavior which can lead to unexpected issues, favoring let and const for better control over variable scope and mutability.

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

## Functions

Declared by `function X() {}`
