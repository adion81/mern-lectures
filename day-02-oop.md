# Day 2 - Object Oriented Programming

<img src="https://github.com/adion81/mern-lectures/blob/master/assets/js.png" alt="JavaScript" width="200px" />

## THE TOP 3.5 WAYS TO MAKE AN OBJECT IN JS!

### 1. just using `{ }`

```javascript
const s1 = {
  bread: "sourdough",
  protein: "bacon",
  isToasted: true,
  toppings: ["avacado", "lettuce", "tomato", "basil pesto aioli"],
  display: function() {
    console.log(`
      This sandwich contains:
      ==================================
      bread:    ${ this.bread }
      protein:  ${ this.protein }
      toasted:  ${ this.isToasted ? "Yes" : "No" }
      toppings: ${ this.toppings.join(", ") }
    `);
  }
};
```

For every object we create we'll have to rewrite all of this.

### 2. using `function() {}`

```javascript
function Sandwich(bread, protein, isToasted, ...toppings) {
  this.bread = bread;
  this.protein = protein;
  this.isToasted = isToasted;
  this.toppings = toppings;
  this.someMethod = function() {
    // TODO: make this method do something
  }
}

const s2 = new Sanwich("sourdough", "bacon", true, "avacado", "lettuce", "tomato", "basil pesto aioli");
```

To make an instance of a `Sandwich` we need to use the `new` keyword. 

### 2.5 prototype methods (like .5 of a way)

If we want to add a display method to the `Sandwich` function above we could declare it inside the function or we can add it on after the fact using a `prototype` method.

```javascript
Sandwich.prototype.display = function() {
  console.log(`
    This sandwich contains:
    ==================================
    bread:    ${ this.bread }
    protein:  ${ this.protein }
    toasted:  ${ this.isToasted ? "Yes" : "No" }
    toppings: ${ this.toppings.join(", ") }
  `);
}
```

### 3.5 using `class`

```javascript
class Sandwich {
  constructor(bread, protein, isToasted, ...toppings) {
    this.bread = bread;
    this.protein = protein;
    this.isToasted = isToasted;
    this.toppings = toppings;
  }
  display() {
    console.log(`
      This sandwich contains:
      ==================================
      bread:    ${ this.bread }
      protein:  ${ this.protein }
      toasted:  ${ this.isToasted ? "Yes" : "No" }
      toppings: ${ this.toppings.join(", ") }
    `);
  }
}

const s2 = new Sanwich("sourdough", "bacon", true, "avacado", "lettuce", "tomato", "basil pesto aioli");
```

When we want to make a class in JS, there are few reasons to not use the `class` syntax introduced in **ES6**.

## Inheritance

What if we wanted to make a Panini... panini's are sandwiches that will always have `isToasted=true`.

```javascript
class Panini extends Sandwich {
  constructor(bread, protein, ...toppings) {
    super(bread, protein, true, ...toppings);
  }
}

const p1 = new Panini("italian", "prosciuto", "mozzarella", "tomato", "basil");
```

