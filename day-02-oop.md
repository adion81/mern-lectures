# Day 2 - Object Oriented Programming

<img src="https://github.com/adion81/mern-lectures/blob/master/assets/js.png" alt="JavaScript" width="200px" />

## THE TOP 3.5 WAYS TO MAKE AN OBJECT IN JS!

### 1. declaring a variable with { }

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

### 2. using function() {}

```javascript
function Sandwich(bread, protein, isToasted, ...toppings) {
  this.bread = bread;
  this.protein = protein;
  this.isToasted = isToasted;
  this.toppings = toppings;
}

const s2 = new Sanwich("sourdough", "bacon", true, "avacado", "lettuce", "tomato", "basil pesto aioli");
```

### 2.5 prototype

If we want to add a display method to the `Sandwich` function we can add it into the above function or we can make is a prototype method.

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

### 3.5 class

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
```

## Inheritance

What if we wanted to make a Panini... panini's are sandwiches where we will always have `isToasted=true`.

```jsavascript
class Panini extends Sandwich {
  constructor(bread, protein, ...toppings) {
    super(bread, protein, true, ...toppings);
  }
}
```
