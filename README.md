## Objectives

- Demonstrate an understandung of object properties and methods.
- Create objects using constructor notation and instances of those objects using the new keyword.
- Compare and contrast creating objects using literal notation vs. constructor notation.

```
Object-oriented programming, also called OOP, is a model for writing computer programs. Before OOP, most programs were a list of instructions that acted on memory in the computer. Instead of a procedural list of actions, OOP is modeled around objects that interact with each other.```
- Wikipedia




OOP is a common pattern throughout many languages. It will enable us to write more readable, organized, and declarative programs. Simply put, understanding Object Oriented Programming will make us better developers.



Let's to create an object

-  1. Object Literal

``` javascript
var turkeyClub = {
  breadType: "sourdough",
  crust: true,
  meat: "turkey",
  veggies: ["lettuce", "tomato"],
  condiments: "mustard"  
}
```

# To do: Let's all make a sandwich

![Alt Text](https://media.giphy.com/media/TQt1xVuNhc9hK/giphy.gif)


### 2 ways to access our property values
. notation 
brackets


## But... is there a more efficient way to do this?

In other words, we should only have to define the properties of a sandwich
one time and then be able to create as many different sandwiches as we
want without repeating ourselves.


Is there a way to use JavaScript to create a template for a sandwich object that we can use
to construct many different sandwiches?




## Introducing the Constructor Function
Constructor function- a way to create an object's baseline blueprint that can be used multiple times without having to redefine the object every time to meet each particular instance's needs. 



``` javascript
function Sandwich(bread, crust, meat, veggies, condiments) {
  this.breadType = bread;
  this.crust = crust;
  this.meat = meat;
  this.veggies = veggies;
  this.condiments = condiments;
}
```
We've introduced a couple new things... what are they?


-  Sandwich starts with a capital letter- ie this serves as an important signal that this function should ONLY be used as a constructor. 

-  `this` - is used in place of the object name to refer to the current object instance.

## Now let's take this framework to create new instances of constructor functions

-  `new` keyword 

``` javascript
var pastramiRye = new Sandwich("rye", false, "pastrami", ["lettuce", "tomato"], "ketchup");
```

``` javascript
var turkeyClub = new Sandwich("sourdough", true, "turkey", ["lettuce", "tomato"], "mustard");
```

``` javascript
var grilledCheese = new Sandwich("white", false, "none", "none", "ketchup");
```

### Objects also allow us to reassign and create new property values

grilledCheese.cheese = "cheddar";
grilledChesse["spices"] = ["cilantro", "paprika"]

### and even delete!

delete grilledCheese.cheese = "cheddar";

## Constructor functions == boss
Creating objects is now MUCH more scalable than if we used literal notation to create every individual object.

Our code will also be cleaner, as we avoid repetition when creating similar objects.


## To Do:
![Alt Text](https://media.giphy.com/media/3o6Zt8Av0cXKAR6MQ8/giphy.gif)

build an animal constructor with 5 properties.
-  using this constructor function making manatee, bear, pig
-  assign an additional unique property to each one
-  delete one of the 5 original five properties per animal



###

# Adding methods to objects 


### 

``` javascript
var superman = {
  // Properties
  firstName: "Clark",
  lastName: "Kent",
  superheroName: "Superman",

  // Method
  revealIdentity: function () {
     console.log(this.firstName + " " + this.lastName + " is " + this.superheroName);
  }
};
``` 

## Let's create more superheros! constructor (and with a method

![Alt Text](https://media.giphy.com/media/PpeGK6edBWAxi/giphy.gif)



Prototypes, and a look at classes:

### Let's take a look at Prototypes and how to construct them (ie Pre-ES6)
#### Simple way to create objects via their prototype

Let's start by creating a new object:
```javascript
var shirt = {size:6, color: "red", gender: "mens", pattern: "plaid" };
```
Now let's build a new object that uses the object we just created (ie shirt) as a prototype: 
``` javascript
var magicShirt = Object.create ( shirt ); // whatever we pass in the parenthese will serve as  the prototype for the new object.
```

If we logged out magicShirt we'd get:
``` javascript
console.log(magicShirt); // Object{size: 6, color: "red", gender: "mens", pattern: "plaid"}
```
magicShirt's properties are **exactly** the same as shirt because it **literally** used shirt and thus inherited all of shirt's properties.

#### Why is this?

An Object inherits from its parent Object, ie its prototype. Each time we create a new Object, that Object automatically has access to all of the properties that were defined in its parent Object. In our shirt example, this means that every single time we make an instance of a new shirt, it has access to all of the properties defined in the original object we created. 

#### Furthermore, we can assign new properties to magicShirt: 
``` javascript
magicShirt.brand = "Gap";
magicShirt.material = "cotton";
magicShirt.usage = "daily";
```
and they'd appear in our magicShirt object:
``` javascript
console.log(magicShirt); // Object{size: 6, color: "red", gender: "mens", pattern: "plaid", brand: "Gap", material: "cotton", usage: "daily"}
```
#### But... this is VERY time consuming, and we know that the more efficient way to create new objects (via use of its prototype) is by the aforementioned Constructor function

# Breaking News! 

## ES6 introduces new gamechanging syntax

Prior to ES6, the common way to build new objects in JavaScript was by using Constructor functions. However Function Constructors can be quite confusing to understand and to help alleviate this, ES6 introduced the "class" keyword. 

Classes in ES6 are honestly just syntactic sugar- they don't add any additional functionality to what we already had in the language (ie constructors), and are just a simpler syntax for building the same objects as we had before.

## Implementing JavaScript's new "class" keyword 

Let's take a look at what a constructor looks like when we use class:

``` javascript
class Pikachu {
  constructor(number, type, fastAttack, chargeAttack, hiddenPower){
    this.number = number;
    this.type = type;
    this.fastAttack = fastAttack;
    this.chargeAttack = chargeAttack;
    this.hiddenPower = hiddenPower;
  }
  walks(){
    return `I'll follow you wherever you go, and I can also do ${this.hiddenPower}!`
  }
}

class Snorlax {
  constructor(number, type, fastAttack, chargeAttack, weight){
    this.number = number;
    this.type = type;
    this.fastAttack = fastAttack;
    this.chargeAttack = chargeAttack;
    this.weight = weight;
  }
  eats(){
    return `Zzzzz! I am massively large and weigh ' + ${this.weight} +' pounds!`
  }
}
```


We see we have two classes: Pikachu and Snorlax. They have some things in common: number, type, fastAttack and chargeAttack. But they also have differences- Pikachu has a hiddenPower attribute and a walking function, whereas Snorlax has a weight attribute and an eats function.  

#### This is fine except...

What if we wanted to create a number of other classes of Pokemon- like Gyarados, Dragonite, Farfetch'd, etc.- all of whom share some of the aforementioned properties but also have their own unique methods or attributes? 

How could we refactor this so that we don't have to keep writing out shared class properties and methods? 

A: Create a base class will abstract this: 
``` javascript
class Pokemon{
  constructor(number, type, fastAttack, chargeAttack){
    this.number = number;
    this.type = type;
    this.fastAttack = fastAttack;
    this.chargeAttack = chargeAttack;
  }
}
```

Here we've defined an Pokemon class. It contains the general properties and methods that can be found in just about all Pokemon. What's great about this is that Snorlax and Pikachu can now just reference this "parent" Pokemon class and thus the only things we'd need to put in their "child" class definitions are the properties and methods that are unique to them.





-  Create ES6 classes.
-  Explain ES6 class inheritance with extends.




# Prototypes

![Alt Text](https://media.giphy.com/media/3o6ZtjDNG2UXy7B3xK/giphy.gif)



# To Do
-  refactor your racer code and create objects.
-  have your new code create 2 racers AND a third (just for show)





