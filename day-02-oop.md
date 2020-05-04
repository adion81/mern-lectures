# Day 2 - Object Oriented Programming

<img src="https://github.com/adion81/mern-lectures/blob/master/assets/js.png" alt="JavaScript" width="200px" />

## THE TOP 3.5 WAYS TO MAKE AN OBJECT IN JS!

### 1. declaring a variable with { }

```javascript
const s1 = {
  bread: "sourdough",
  protein: "bacon",
  isToasted: true,
  toppings: ["avacado", "lettuce", "tomato", "basil pesto aioli"]
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

### 3.5 class
