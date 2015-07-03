#Javascript Objects

##What is an Object
* A container for values in the form of __properties__ and functionality in the form of __methods__.
* Objects provide functionality through methods.
### Methods
* A method is on an object. e.g.
```console.log('hi')
```
 the console object is calling the log method.
* A function is independent of an object.
* A method call __may__ or __maynot__ return a value e.g.
``` document.getElementById('header')``` => returns the header element which is an object.
```console.log('test')``` => does not return anything

* A var can be an object
```
var a = 22
typeof a => number
var b = document.getElementById('header');
typeof b => object
```
### Properties
* You can get and set property values
```
var b = document.getElementById('header');
b.innerHTML => gets the value of the innerHTML property
```
```
	b.innerHTML = 'Some stuff' => is setting the value of the innerHTML property
```
* Properties store data
* The name of a property is it's __key__
* The contents of a property is it's __value__

##Types of Objects
###Native Objects
* No matter where you JavaScript is run it will always have these objects
  * Number, String, Array, Boolean, Object and many more
###Host Objects in the Browser
* These are provided by the environment where JavaScript is run e.g. your specific browser.
  * document, console,  Element are examples of these in your browser but you won't find these in node.js.
###Your Own Objects
* Anything you create in you programming. This allows you to model things in real life.
* All realworld objects have __state__ and __behaviour__
* State is the __condition__ of all values at a __particular__ point of time e.g. a radio object's state can be either on or off
```radio.on => true```
  * You change the state either directly or through a method call.
	``` radio.on = false```
	* An objects state is stored in it's __properties__
* Behavior is stored in it's __methods__
###Encapsulation
Putting objects in code allows you to hide the complexity of an object from another developers and to organise everything about that together.
* e.g. a radio object when you call the change station method you don't know how the code changes the station, this is hidden you just call this method to move the station.

##Object Literal
Stores the state of a thing. It is a list of key/value pairs wrapped in curly brackets. This is a common way to create objects e.g.
```
var person = {
	name: "Jim",
	coder: "yes"
};
person.name; => Jim
person.code; => yes
```
Or you could use the key value. All keys are strings in JavaScript
```
person["name"] => Jim
person["coder"] => yes
```
###Add methods to an Object Literal
```
var dice = {
	roll: function() {
		var sides = 6
		var randomNumber = Math.floor(Math.random() * sides) + 1
		console.log(randomNumber);
	}
};
```
The object dice now has a roll method and we can call it like this ```dice.roll()``` we have Encapsulated the roll behavior too.

####this
* Is the owner of function where the method is called. E.g. this object dice has a roll function and a property sides. The roll function is trying to use sides and will look in it's local function scope but it is not there. Next the interpreter will look in the global scope and its not there either.

```
var dice = {
	var sides = 6
	roll: function() {
		var randomNumber = Math.floor(Math.random() * sides) + 1
		console.log(randomNumber);
	}
};
```
Sides is a property on dice. To fix this we need to tell the interpreter to look at the sides property on object dice with
```
var randomNumber = Math.floor(Math.random() * dice.sides) + 1
```
The problem is that an object can have more than one function, what if rename the dice object to dice_sides_10 we have to rename this for all the called dice properties.
The solution is to use 'this'
```
var randomNumber = Math.floor(Math.random() * this.sides) + 1
```
Note that the meaning of 'this' can change depending on how you use it. It is the object that owns the method that is being called.
