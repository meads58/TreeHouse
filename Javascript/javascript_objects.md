#Javascript Objects

##What is an Object
* A container for values in the form of __properties__ and functionality in the form of __methods__.
###Methods
* A method is on an object. e.g.
	```console.log('hi')''' the console object is calling the log method.
* A function is independent of an object.
* A method call may of maynot return a value e.g.
``` document.getElementById('header') => returns the header element which is an object
	console.log('test') => does not return anything
```
* A var can be an object
``` var a = 22
	typeof a => number
	var b = document.getElementById('header');
	typeof b => object
```
###Properties
* You can get and set property values
```var b = document.getElementById('header');
	b.innerHTML => gets the value of the innerHTML property
	b.innerHTML = 'Some stuff' => is setting the value of the innerHTML property