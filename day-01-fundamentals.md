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

     var num = 19; // this var num is only accessible with in the function eatBanana, it is also a different variable than the one declared up above.

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

It's important to know that hoisting only works on the var key word.  let and const do not get hoisted.<br>
<br>
When we declare variables with `var`, they get hoisted to the top of the file or function.

```js
console.log(name);//This will print out undefined.

function doSomething(){
    console.log(pudding);// This will print out undefined.
    for(let i = 0; i < 10; i++){
        var pudding = "fruity pebbles";
    }
}

var name = "Mr. Nibbles";
console.log(name); // This will print out Mr. Nibbles.
```


### Destructuring

Destructuring is a fancy expression that allows us to unpack values from arrays and properties from objects into their own distinct variables.

#### Array Destructuring

We can pull variables out of an array and assign them to others in one single line.<br>
We can also selected which indices we want to pull from by using `,` when we declare our variables.<br>
With arrays we can name our new variables anything we want.

```js

var instructors = ["Will","Adrien","Anne","Phil"];

// Old way . . .
var first = instructors[0];
var third = instructors[2];
var fourth = instructors[3];

// or . . . 

// Destructuring syntax
var [first,,third,fourth] = instructors;

```

#### Object Destructuring

With objects we need to call the key names within the destructure brackets in order to pull the values out.

```js

var spaceCrab = {
    name : "Obi WanCrabnobi",
    weapon: "Claw Light Saber",
    isWanted: false,
    spaceCraft : "Alluminum Falcon"
}

// Old way . . . 
var name = spaceCrab.name;
var spaceCraft = spaceCrab.spaceCrab;

// or . . . 

// Destructured syntax 
// These variable names must match up to the key names in the object.
var { name , spaceCraft } = spaceCrab;

// If we want to assign a new variable name
var { ship : spaceCraft } = spaceCrab;

```






