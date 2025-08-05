# JavaScript Advance Summary

## Versions of JS
ES5 earlier - have var
ES6 later - have let and const

We're using both the versions thus have all 3

## Browser Context API

Offers:
  - Window object: properties of browser
  - Stack: stores function call
  - Heap Memory: stores temporary variables

## Execution Context
Execution Context is the environment (container) in which JavaScript code is evaluated and executed. \
It's always created when a function is called.\
Conatins:
  - Variables
  - Child Function
  - Lexical Env: Stores scope and scope chain
`scope chain: function can access what values i.e. a hierarchical structure that determines the accessibility of variables and functions within a program.`
```cpp
Execution Context {
  Lexical Environment {
    Environment Record {
      variable1: value,
      function inner() {...}, // ✅ child function
    },
    Outer: reference to parent LE
  },
  this: depends on how function is called
}

```

## ForEach, For...in, For...of

| Loop Type   | Works On                                | Iterates Over         | Use Case                              |  
| ----------- | --------------------------------------- | --------------------- | ------------------------------------- |
| `forEach()` | Arrays                                  | Values                | Array value processing                |
| `for...in`  | Objects (and arrays, but not preferred) | Keys (property names) | Object property traversal             |           
| `for...of`  | Iterables (arrays, strings, sets)       | Values                | Loop through array or iterable values |          

- arr.forEach(func(val))- function will be called for each elements in arrays.
  note that the forEach doesn't change values of Array, instead "val" creates a temp copy of each element in that array
can also write it as:
```js
arr.forEach((num) => {
  console.log(num); // 1 2 3
});
```
- for(let x in obj){  function(x)  }


## Sync & Async

- Synchronous: Code runs line by line, each step waits for the previous one to finish.
- Asynchronous: Code runs without waiting, allowing delayed tasks to complete later.\
  *JavaScript is single-threaded — it can do only one thing at a time.
But with asynchronous code, JS can start a task, then move on without waiting, and handle the result later.*

  We use async when using these setInterval(), setTimeout(), Promises, Fetch, Axios, XMLHttpsRequest
  ### Why? When we click on something or tells the browser to do some task, that can be asking some otehr server to fetch something, then if itr takes time, then we won't be able to do any other thing is the webpage will be freezed until the task is done, thus we use async, so that till we get the output of that task, we can still run or do other things on the webpage

  
**Tools Used for Asynchronous JavaScript**\

1. setTimeout() — Run After a Delay
```js
   setTimeout(() => { ... }, X);       // ... Callback functions
```
Executes code after X milliseconds.
2. setInterval() — Repeat at Intervals
```js
setInterval(() => { ... }, X);
```
Executes code repeatedly every X milliseconds.\
This runs forever every second unless stopped with clearInterval().

3. Promises — Handle Future Results
4. Fetch - Sends a request to get data (returns Promise)
4. await, async
   - await pauses the function until the Promise is resolved.
   - Use try...catch to handle errors in async functions.
