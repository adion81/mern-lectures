# Day 6 - Mapping and Conditionals

<img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/React-icon.svg" width="256px" alt="React" />

## Promises - A better way for async behavior.

A `Promise` is a design pattern that we can use to get information when we don't know how long it will take to get it.<br>
<br>
A `Promise` has three different stages.<br>
<ol>
    <li>Pending</li>
    <li>Resolved</li>
    <li>Rejected</li>
</ol>

We can create a `Promise` like so . . .

```javascript
const orderSandwich = new Promise((resolve,reject) => {
    let deliveryMixup = Math.floor(Math.random()* 100);
    let outOfSandwich = Math.floor(Math.random()*100);
    if( deliveryMixup <= 20 || outOfSandwich <= 5){
        reject("Oops, something happened to your sandwich");
    }
    else{
        resolve("Let's Eat!!!")
    }
});

orderSandwich // This promise will either come back resolved or rejected.
    .then(res => console.log(res)) // This is when your Promise is resolved.
    .catch(err => console.log(err))// This is when your Promise is rejected.
```

## APIs

## Use Effect Hook

