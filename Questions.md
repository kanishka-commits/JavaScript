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

