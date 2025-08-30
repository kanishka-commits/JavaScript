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


