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

## APIs - Application Programming Interface
APIs are a set of rules that allow programs to talk to each other.

### Restful APIs
RESTful APIs is a set of rules to shape what the API looks like.<br>
<br>
REST - `Representational State Transfer`<br>
<br>
<h6>The most important rule of RESTful APIs is that you should get a piece of data called a resource from a specific url.</h6>

### Consuming APIs
A great way to consume an API is using the fetch method within JS.<br>
`fetch() is a Promise`

```javascript
fetch("https://official-joke-api.appspot.com/random_joke")
    .then(res => response.json())
    .then(res => {
        //do something with the data coming back.
        // maybe set it into state???
        console.log(res);
    })
    .catch(err => console.log(err));
```

Whilst fetch is great to consume APIs, but there is a better third party library called `Axios`.<br>
<br>
We must install it and import it in order to use it.<br>
`npm install axios`

```javascript
import axios from 'axios';

axios.get('https://official-joke-api.appspot.com/random_joke')
    .then(res => {
        //do something with the data coming back.
        // maybe set it into state???
        console.log(res.data);
    })
    .catch(err => console.log(err))

```

In order to invoke these API calls we could put them into a function and call the function when we click a button.<br>
But what if we wanted to call the API when the page is first loaded?


## Use Effect Hook


