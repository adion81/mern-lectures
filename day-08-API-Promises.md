# Day 8 - APIs and Promises
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

useEffect is a React hook that can manage side effects in our functional components.<br>
It gets called everytime the component is rendered, and we can use it to call an api when the page first gets loaded.<br>
<br>
The first argument in the `useEffect` hook is an anonymous function, and we write what we want to happen inside of it.<br>
The second argument in the `useEffect` hook is an array that contains variables.<br>
This is an extremely important argument, because you don't want to end up calling your api 5 million times.<br>

```javascript
import React,{useState,useEffect} from 'react';
import axios from 'axios';

function App(){
    const [joke,setJoke] = useState({});

    useEffect(() => {
        axios.get('https://official-joke-api.appspot.com/random_joke')
            .then(res => setJoke(res.data))
    },[]);


    return (
        <div>
            <h4>{joke.setup}</h4>
            <p>{joke.punchline}</p>
        </div>
    );
}
export default App;
```

<h2>If the second argument array is empty, then the useEffect hook will only execute once when the component first renders.<h2>
