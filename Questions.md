Nested loop for 3*3 grid

```js
let i=1,n=3;

for(let row=0;row<n;row++){
    let str="";
    for(let col=0;col<n;col++){
        str+=`${i} `
        i++;
    }

    console.log(str);
}
```

Why sometimes we use for (var i=...) and other times for (let i=...)

```js
for (let j = 0; j < 3; j++) {
  console.log("Inside loop:", j);
}
console.log("Outside loop:", j); // ❌ Error (j is not defined)
```

Bt when we use VAR, we can access j 


## Var vs Let
```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
```
- var → function-scoped, shared across loop iterations
- let → block-scoped, creates a new binding per iteration

## this keyword

```js
let obj = {
  name: "Bob",
  sayHi: function() {
    setTimeout(() => {
      console.log(this.name);
    }, 1000);
  }
};

obj.sayHi();  // "Bob"
```
`Arrow functions don’t have their own this; they inherit it from the surrounding scope (sayHi method). So here, this still refers to obj.`


```js
let obj = {
  name: "Bob",
  sayHi: function () {
    setTimeout(function () {
      console.log(this.name);
    }, 1000);
  }
};

obj.sayHi();
```
`Note: setTimeout is just a normal function call, not a method of obj. (even tho it's called inside a method function) thus 'this' inside a nrml function call is global/undefined only`

```js
let person = {
  name: "Alice",
  greet: function () {
    function inner() {
      console.log(this.name);
    }
    inner();
  }
};

person.greet(); //undefined
```
`Note: Because inner() is a normal function call, not tied to person.`

```js
let person = {
  name: "Alice",
  greet: function () {
    let inner = () => {
      console.log(this.name);
    }
    inner();
  }
};

person.greet(); //Alice

```
`Note: Because arrow captures this from greet, which is bound to person.`

```js
let user = {
  name: "Bob",
  sayHi() {
    console.log(this.name);
  }
};

let f = user.sayHi.bind(user);
f(); // Bob
```

`Note: Because bind forces this to always be user.`


**This in callback functions**
```js
let obj = {
  name: "Context",
  say() {
    [1, 2, 3].forEach(function (n) {
      console.log(this.name, n);
    });
  }
};

obj.say();

O/P
undefined 1
undefined 2
undefined 3
```

*FIX*
```js
let obj = {
  name: "Context",
  say() {
    [1, 2, 3].forEach((n) => {
      console.log(this.name, n);
    });
  }
};

obj.say();

O/P
Context 1
Context 2
Context 3

```

**With NEW keyword**
```
function User(name) {
  this.name = name;
}

let u1 = new User("Dave");
console.log(u1.name);

let u2 = User("Eve"); // Dave
console.log(u2); //undefined
```

## Rest & Spread
```js
function sum(...nums) {
  return nums.reduce((a,b) => a+b, 0);
}
console.log(sum(1,2,3,4));
```
## const Object Mutation
```js
const obj = { a: 1 };
obj.a = 2;
obj.b = 3;
console.log(obj); //{ a: 2, b: 3 }
```
const prevents reassignment of the variable, but object properties can be changed.

## Questions

Q1. `console.log(0.1 + 0.2 === 0.3);`

👉 Output: false
✔ Because of floating-point precision, 0.1 + 0.2 = 0.30000000000000004.

Q2.`console.log(typeof NaN);`
👉 Output: "number"
✔ NaN means Not-a-Number, but its type is still "number" in JS.

Q3.`console.log([1, 2, 3] + [4, 5, 6]);`
👉 Output: "1,2,34,5,6"
✔ Arrays are converted to strings when using +.

Q4.
```js
let a = { x: 1 };
let b = a;
b.x = 2;
console.log(a.x);
```
👉 Output: 2
✔ Objects are reference types. b points to the same object as a.

Q5.`console.log([] == ![]);`
👉 Output: true
✔ ![] → false. Then [] == false.
During coercion, [] → "" → 0.
false → 0.
So 0 == 0 → true.

Q6.
```js
(function() {
  var a = b = 5;
})();
console.log(typeof b);
console.log(typeof a);
```
👉 Output:
"number"
"undefined"
✔ Inside IIFE: b = 5 makes b global (since no var/let/const).
But a is local to function, not accessible outside.

Q7.
```js
console.log("5" - 3);
console.log("5" + 3);
```
👉 Output:
2
"53"
✔ - forces type coercion to number.
✔ + with string does concatenation.

Q8.
```js
let obj = { a: 100 };
console.log(obj.toString());
```
👉 Output: "[object Object]"
✔ Default toString() for plain objects.

eg: 
```js
console.log(obj); // { a: 1, b: 2 }
console.log(obj + ""); // [object Object]
```
The second one becomes "[object Object]" because the object gets converted into a string using .toString().

```js
console.log(JSON.stringify(obj)); 
// {"a":1,"b":2}
```

Q9.
```js
console.log(null == undefined);
console.log(null === undefined);
```
👉 Output:
true
false
✔ == does type coercion → null loosely equals undefined.
✔ === checks strict equality (different types).

Q10.
```js
console.log([1, 2, 3].map(num => {
  if (num > 1) return;
  return num * 2;
}));
```
👉 Output: [2, undefined, undefined]
✔ For 1 → returns 1*2 = 2.
✔ For 2 and 3 → condition num > 1 is true, so it returns undefined.

Q11.
```js
var a = 10
(function () {
  console.log(a); 
  a = 20;
})();

//is same as: 
(function () {
  var a;          // hoisted, initialized as undefined
  console.log(a); // logs undefined
  a = 20;
})();
```

Q12.
```js
console.log("start");
async function test() {
  console.log("inside");
  return "done";
}
test().then(console.log);
console.log("end");
```
Output
```
start
inside
end
done
```

why? sync function start, then sync inside, then it return a promise thus goes to microtask, then end as its' async and at end, done

Q13.
```js
// Q2
setTimeout(() => console.log("1"), 0);

Promise.resolve().then(() => {
  console.log("2");
  setTimeout(() => console.log("3"), 0);
});

console.log("4");

// Answer:
// 4
// 2
// 1
// 3
```

Q14,
```js
// Q5
setTimeout(() => console.log("outer"), 0);

Promise.resolve().then(() => {
  console.log("inner");
  setTimeout(() => console.log("nested"), 0);
});

// Answer:
// inner
// outer
// nested
```

Q15,
```js
console.log("M");
setTimeout(() => console.log("N"), 0);
(async function() {
  console.log("O");
  await null;
  console.log("P");
})();
console.log("Q");

// Answer:
// M
// O
// Q
// P
// N
```

Q16,
```js
async function foo() {
  console.log("X");
  await null;
  console.log("Y");
}
console.log("Z");
foo();
(async function c() {
  console.log("iife");
})();
console.log("W");

/* Answer
Z
X
iife
W
Y
*/
```
