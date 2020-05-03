# Day 1 - JavaScript Fundamentals



<img src="https://github.com/adion81/mern-lectures/blob/master/assets/js.png" alt="JavaScript" width="200px" />

JavaScript was invented in 1995 by this guy . . . 

#### Brendan Eich
<img src="https://peoplepill.com/media/people/thumbs/B/brendan-eich.jpg" src="Brendan Eich" width="200px">

He built it whilst working at Netscape, to give web pages a dynamic ability.

## JS Basics

### Variables & Data Sets

In JS we declare variables with the `var` keyword.

```js
// This is a number.
var number = 1;

//This is a string.
var name = "Benny Bob";

//This is a boolean.
var isWorking = true;

//This is an array with different variable types.
var arr = [1,3,6,"Mr. Nibbles",true];

//This is an object
var dojo = {
    instructors: ["Will","Adrien"],
    numberOfNinjas: 50,
    stack : "MERN"
}
```


### Notation

In JS we can refer to object values in two different ways:

<ol>
    <li>Dot Notation</li>
    <li>Bracket Notation</li>
</ol>

For the most part, we will be using dotnotation.

### Scoping 

<img src="https://miro.medium.com/max/640/1*Xc7vCmdjT3ImRnW1knnCbw.png" alt="scoping" width="400px">

`var` isn't the only keyword we can use to define variables.<br>
We can also use `let` and `const`.<br>

There are three different scopes:

<ol>
    <li>Global - we use <b style="color:blue;">var</b></li>
    <li>Function - we also use <b style="color:blue;">var</b></li>
    <li>Block - we use <b style="color:blue;">let</b> and <b style="color:blue;">const</b></li>
</ol>


#### index.js
```js
 var num = "banana";//This var num is accessible anywhere with in the index file.

 function eatBanana(){
     var num = 19; // this var num is only accessible with in the function eatBanana
     for(let i = 0; i < num; i++){
         // We can print i + num here and get it's value
         console.log(i + num);
     }
     //If we print out i here, we will get a reference error.
     console.log(i);
     if(num == 19)
     {
         let sum = num + num;//sum is only available within the if statement.
     }
 }
 eatBanana();

```

But what about the `const`key word?

The difference between  `let` and `const` is that const won't be reassigned and let maybe reassigned.

### Hoisting



