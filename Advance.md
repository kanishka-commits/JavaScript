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
  
## Promiese
They're are used to handle asynchronous operations in JavaScript, such as fetching data from an API, reading files, or setting timers.\
Before promises, asynchronous code was managed using callbacks, which often led to callback hell—deeply nested, hard-to-read code.\

It's an object that represents the eventual completion (or failure) of an asynchronous operation.\

States of a Promise:
  - Pending – Initial state, operation not yet completed.
  - Fulfilled – Operation completed successfully (resolve() called).
  - Rejected – Operation failed (reject() called).
  - Settled – Promise is either fulfilled or rejected.
```js
const promise = new Promise((resolve, reject) => {
  // async operation here
});
```

| Method      | Purpose                                             |
| ----------- | --------------------------------------------------- |
| `then()`    | Executes when the promise is fulfilled.             |
| `catch()`   | Executes when the promise is rejected.              |
| `finally()` | (Optional) Executes after fulfillment or rejection. |


  
## IIFE (Immediately Invoked Function Expression) or Self-invoking function
An IIFE is a function that runs immediately after it is defined, without needing to be called later.

```js
(function() {
  // Code inside runs immediately
})();
```
Variables inside IIFE can’t be accessed from outside.\
Useful for one-time execution (like initialization, hiding data, etc.)\

Helpful  for things like:
```js
const CounterModule = (function () {
  let count = 0; // 🔒 private variable

  return {
    increment: function () {
      count++;
      console.log("Count:", count);
    },
    decrement: function () {
      count--;
      console.log("Count:", count);
    },
    getCount: function () {
      return count;
    }
  };
})();
```
We can create it using nrml functiona also but we'll need not to "call" ir, directly call "CounterModule.increment()" like this
## Strict Mode
In 'Strict mode,' however, all forms of errors, including silent errors, will be thrown. As a result, debugging becomes a lot simpler.\

The 'use strict' keyword is used to define strict mode at the start of the script. Strict mode is supported by all browsers.\
Engineers will not be allowed to create global variables in 'Strict Mode.\

## this keyword

The “this” keyword refers to the **object** that the function is a property of.

```js
function doSomething() {
  console.log(this);
}
   
doSomething();  
```
returns *window object*, because, the doSomething is property fof window object

```js
var obj = {
    name:  "vivek",
    getName: function(){
    console.log(this.name);
  }
}
   
obj.getName();
```

returns *obj* object

also
```js
var obj = {
  name: "vivek",
  getName: function() {
    console.log(this.name);
  }
};

var getName = obj.getName; //The getName function is copied (not called yet), and stored in a variable.

var obj2 = { name: "akshay", getName }; 

obj2.getName(); // akshay
```

## call(), apply() and, bind() methods

The value of `this` depends on how a function is called, not where it is defined.\
Sometimes, you want to manually control the value of this inside a function — that's where call(), apply(), and bind() come in.


- call()
  - This method invokes a method (function) by specifying the owner object.
  - call() method allows an object to use the method (function) of another object.
  - Manual this, quick call.
  - `func.call(Object, arg1, arg2, ...)`
- apply() is exactly like call(), except it takes arguments as an array.
  `func.apply(thisArg, [arg1, arg2, ...])`
- bind()
  - does NOT call the function immediately.
  - It returns a new function with the same body, but with this permanently bound.
  - Save this for future use (e.g., callbacks)
  - `let boundFunc = func.bind(thisArg, arg1, arg2, ...);`
 
  - eg:
   ```js
   const greetKanishka = greet.bind(user, "Hey", "!!"); //user is an object

    greetKanishka();  // Output: Hey, Kanishka!!

    ```


## RegExp stands for Regular Expression
- a pattern-matching tool used to search, extract, and manipulate strings.
- There are 2 ways to create them:
1. Using literal syntax:`const pattern = /hello/;`
2. Using constructor: `const pattern = new RegExp("hello");`

Real life eg: validating an email and a strong password during signup.
  - We'll use **exec ()** to search a string for a specific pattern, and if it finds it, it'll return the pattern directly; else, it'll return an 'empty' result.
  - We will use a **test ()** to find a string for a specific pattern. It will return the Boolean value 'true' on finding the given text otherwise, it will return 'false'.

## Currying in JavaScript
It's a technique in JavaScript (and functional programming) where:
A function with multiple arguments is transformed into a series of functions each taking a less no of argument. (can be one, can be more)

eg:
Instead of writing:
```js
function add(a, b) { return a + b; }
```
We curry it like this:

```js
function add(a) {
  return function(b) { return a + b; };
}
console.log(add(2)(3)); // ➡️ 5
```

For arrow functions: 
`const add = a => b => a + b;`

## Closure
A closure is formed when a function remembers and accesses the variables from its outer scope, even after that outer function has finished running.


**A closure lets a function "remember" and "use" variables from where it was created, not where it was called.**\
Useful in:
  - Data hiding / Encapsulation
  - Private variables in JavaScript
  - Once-only initialization (like setting up something once)
  - Currying, memoization, event handlers

## Memoization
BY using memoization we can store(cache) the computed results based on the parameters. If the same parameter is used again while invoking the function, instead of computing the result, we directly return the stored (cached) value.

`Although using memoization saves time, it results in larger consumption of memory since we are storing all the computed results.`


## Constructor functions
Used to create objects in javascript.\

USage: If we want to create multiple objects having similar properties and methods, constructor functions are used.\

Note- The name of a constructor function should always be written in Pascal Notation: every word should start with a capital letter.\

*Classes* are syntactic sugars for constructor functions. They provide a new way of declaring constructor functions in javascript.

`syntactic sugars syntax within a programming language that is designed to make things easier to read or write. It doesn’t add new functionality,`

## DOM
DOM stands for Document Object Model.  DOM is a programming interface for HTML and XML documents.\
When the browser tries to render an HTML document, it creates an object based on the HTML document called DOM. Using this DOM, we can manipulate or change various elements inside the HTML document.\

## BOM
BOM stands for Browser Object Model.\
It allows JavaScript to interact with the browser (not just the webpage).\

Unlike the DOM (Document Object Model), which interacts with the content of the web page, the BOM interacts with the browser environment.\


| Feature          | **BOM (Browser Object Model)**                             | **DOM (Document Object Model)**                         |
| ---------------- | ---------------------------------------------------------- | ------------------------------------------------------- |
| **Purpose**      | Interacts with the **browser** itself                      | Interacts with the **webpage content (HTML)**           |
| **Root Object**  | `window`                                                   | `document`                                              |
| **Main Focus**   | Controls browser features (e.g., location, history)        | Accesses and manipulates webpage structure/content      |
| **Examples**     | `window.alert()`, `window.location.href`, `window.history` | `document.getElementById()`, `document.querySelector()` |
| **Use Case**     | Reloading page, getting screen info, navigating history    | Adding elements, changing text, styling, etc.           |
| **Control Over** | Browser tabs, URL, popup windows, screen size, etc.        | HTML elements, attributes, styles, and structure        |
| **Part of**      | Not standardized — it's browser-dependent                  | Standardized by W3C                                     |

## Client and Server side
| Feature            | **Client-Side**                                   | **Server-Side**                                       |
| ------------------ | ------------------------------------------------- | ----------------------------------------------------- |
| **Runs On**        | User’s **browser** (e.g., Chrome, Firefox)        | **Web server** (e.g., Node.js, Apache)                |
| **Languages Used** | HTML, CSS, JavaScript                             | Node.js, PHP, Python, Ruby, Java, etc.                |
| **Access To**      | DOM, browser APIs, local storage, UI rendering    | Databases, authentication, file systems, server logic |
| **Speed**          | Fast (no need to contact server)                  | Slower (due to network and processing time)           |
| **Security**       | Less secure (can be viewed and modified by users) | More secure (code is hidden from users)               |
| **Examples**       | Form validation, animations, UI interactions      | Login handling, data processing, database queries     |
| **Visibility**     | Code is **visible** in browser dev tools          | Code is **hidden** from the end user                  |

Client-side: Everything you see and interact with — buttons, forms, animations.\
Server-side: Everything that happens behind the scenes — storing data, verifying login, sending emails.\


