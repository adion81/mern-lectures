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

### Rest/Spread

There is a new operator is town ...<br>
<br>
Actually that's it!!!  `...`<br>

It called the rest/spread operator, and it allows us to get the rest of a data structure or spread content of an existing one.<br>

```js
var instructors = ["Will","Adrien","Anne","Phil"];

const [first,second,...others] = instructors;

// This will print out an array with ["Anne","Phil"]
console.log(others);

var spaceCrab = {
    name : "Obi WanCrabnobi",
    weapon: "Claw Light Saber",
    isWanted: false,
    spaceCraft : "Alluminum Falcon"
}

// This will assign the name to obi, and make a new object with the rest of spaceCrab attributes to a variable called info.
const { obi: name , ...info } = spaceCrab;

```

### Arrow Functions

Arrow functions are a simplified way we can write an anonymous function.<br>

```js

function add(num1,num2){
    var sum = num1 + num2;
    return sum
}

// We can rewrite the function above in a one line wonder arrow function!

var sum = (num1,num2) => num1 + num2;

var spaceCrab = {
    name : "Obi WanCrabnobi",
    weapon: "Claw Light Saber",
    isWanted: false,
    spaceCraft : "Alluminum Falcon"
}

// We can also create an arrow function to print out the info of spaceCrab.

const printInfo = (spaceCrab) => {
    console.log("Name: " + spaceCrab.name);
    console.log("Weapon: " + spaceCrab.weapon);
    console.log("Wanted ?: " + spaceCrab.isWanted);
    console.log("Ship: " + spaceCrab.spaceCraft);
}

// And if we wanted to simplify it to one line . . . 
const printInfo = (spaceCrab) => console.log(`Name: ${spaceCrab.name}\nWeapon: ${spaceCrab.weapon}\nWanted ?: ${spaceCrab.isWanted}\nShip: ${spaceCrab.spaceCraft}`);
```

### Ternary Operator

Well it loos like we are starting to become one line wonders in JS!<br>
<br>
What if there was a way that we could write a simple if/else statement in one line?<br>
<h1>WONDER NO MORE!!!</h1>

We can do this with a ternary operator . . .

`{is this condition true} ? {do something if true} : {do something if false}`

```js

var isDarkSide = true;

isDarkSide ? console.log("Now your journey to the dark side is complete") : console.log("You will join us or die!!!");

```



