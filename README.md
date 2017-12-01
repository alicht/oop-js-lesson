### LEARNING OBJECTIVES
*After this lesson, you will be able to:*

- Demonstrate a working knowledge of object properties and methods.
- Create objects using constructor notation and instances of those objects using the new keyword.
- Compare and contrast creating objects using literal notation vs. constructor notation.
- Define methods on custom objects by attaching them to the prototype.
- Understand object inheritance.

Objects have both data and behavior.
First part of our lesson = data

# Objects in JS

-  1. Object Literal

``` javascript
var turkeyClub = {
  breadType: "sourdough",
  crust: true,
  meat: ["turkey", "bacon"],
  condiments: "mayo",
  veggies: ["lettuce", "tomato"],
  cheese: "cheddar"
}
```
In object-oriented programming, we use objects to represent logical and
often physical concepts, such as students, books, and even delicious
sandwiches. In object-oriented programming (OOP), our objects should
not only allow us to encapsulate data (i.e. gather and store values
that are attributes of the object, such as meat and condiments in a
sandwich), but also allow us to reuse the data structure without
constantly redefining it.


In other words, we should only have to define the properties of a sandwich
one time and then be able to create as many different sandwiches as we
want without repeating ourselves.
Is there a way to use JavaScript to create a template for a sandwich object that we can use
to construct many different sandwiches?

## CONSTRUCTOR FUNCTION

``` javascript
function Sandwich(bread, crust, meat, condiments, veggies, cheese) {
  this.breadType = bread;
  this.crust = crust;
  this.meat = meat;
  this.condiments = condiments;
  this.veggies = veggies;
  this.cheese = cheese;
}
```
You'll notice the name of the constructor function Sandwich starts with a capital letter. This is important. While the capitalization of a function does not affect how it behaves, it serves as an important signal to our fellow programmers that this function should ONLY be used as a constructor. Adhering to this convention is a good way to communicate intent to other developers who may have to maintain this code

## creating instances of constructor functions

var blt = new Sandwich("white", false, "bacon", "mayo", ["lettuce", "tomato"], "none");
 
var turkeyClub = new Sandwich("sourdough", true, ["turkey", "bacon"], "mayo", ["lettuce", "tomato"], "cheddar");
 
var grilledCheese = new Sandwich("white", false, "none", "none", "none", "cheddar");

### 2 ways to access these property values
. notation 
brackets

### reassign property values

grilledCheese["meat"] = "bacon";


To Do:

build an animal constructor with 5 properties.
-  using this constructor function making manatee, bear, pig

![Alt Text](https://media.giphy.com/media/3o6Zt8Av0cXKAR6MQ8/giphy.gif)
-  



=======

second part = behavior


Board: let's write 


In object-oriented programming, we use objects to represent logical and
often physical concepts, such as students, books, and even delicious
sandwiches. In object-oriented programming (OOP), our objects should
not only allow us to encapsulate data (i.e. gather and store values
that are attributes of the object, such as meat and condiments in a
sandwich), but also allow us to reuse the data structure without
constantly redefining it.
In other words, we should only have to define the properties of a sandwich
one time and then be able to create as many different sandwiches as we
want without repeating ourselves.
Is there a way to use JavaScript to create a template for a sandwich object that we can use
to construct many different sandwiches?

Lab:
Create a constructor function for each of the following:
Dog with name, breed, and age properties
Cat with name, breed, and age properties
Bird with name, breed, age,  properties

Classes:


-  Explain what a method is and the difference between a method and a function.
-  Add an action to a constructor function.
-  Explain what this is in the context of an object.
-  Create ES6 classes.
-  Explain ES6 class inheritance with extends.




