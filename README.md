## Variables
**You can write var with letters, numbers, underscores and dollar sign, but the first sign had to be a letter or dollar sign.**

```javascript

// Examples name of vars
var n2_0 = 'red';
var myNum = 30;
var &width = 300;

// type number
var i = 35;

// type string
var i = 'nice var';

```

## Dom Manipulation

**Handled HTML Elements**

```javascript
// ID
document.getElementById("nameOfID");
// TAG HTML
document.getElementsByTagName("p");
// CLASS CSS
document.getElementsByClassName("nameOfClass");

```

**Elements of document**

``` javascript
// BODY
document.body
// TITLE'S DOM
document.title
// ALL IMAGES'S DOM
document.images
// ALL LINKS'S DOM
document.links
// ALL SCRIPTS'S DOM
document.scripts
```

## Style
**Apply propeties css by js **
*element + style + propertie css + value css*

``` javascript
document.body.style.background = "red";

```


## Functions
**Auto-execute javascript functions AND call them later**

```javascript
(function(){

// here your functions auto-executed

}());

```

## Arrays
**Multiple values in one var.**

```javascript
// Array
var colors = ['red', 'blue' 'purple']
```

Position of a element in array

```javascript
// Choose purple element of this array
var colors = ['red', 'blue' 'purple'];
colors[2];
```

Change value of a element of array

```javascript
// Purple will be green
var colors = ['red', 'blue' 'purple'];
colors[2] = 'green';
```

How many values are in an Array

```javascript
// length propertie
var colors = ['red', 'blue', 'purple', 'cyan', 'skyblue'];
colors.length;
```

Show the inverse values of an Array

```javascript
// reverse propertie
var colors = ['red', 'blue', 'purple', 'cyan', 'skyblue'];
colors.reverse();
```

## Loops
**Repite acctions**

### The FOR loop

```javascript
// Repeat x times an action
for (var i=0; i<10; i++ ){
   console.log('this time is ' + i);
};
```


```javascript
// Execute a provided function once per array element.
var funArray = [11, 27, 38, 42, 57];
for (var i=0; i < funArray.length; i++ ){
   console.log(funArray[i]);
};
```

### The While loop

```javascript
// Repeat an action while a condition
var i = 0; 
while ( i < 10) { 
   console.log(i++)
}
```

### The forEach loop

```javascript
// Execute a provided function once per array element.
var funArray = [11, 27, 38, 42, 57];
funArray.forEach( function(i) {
   console.log(i);
});
```

## Conditionals
**Conditionals power**

### if

```javascript
// If it's equal
var i = 2;
if(i == 2){
console.log('yes,' +i+ ' is equal 2');
}
```

```javascript
// If it's not equal
var i = 2;
if(i != 4){
console.log('You are right,' +i+ ' is not equal 4');
};
```

### if else

```javascript
// If it's not equal
var i = 4;
if(i != 4){
  console.log('You are right, ' +i+ ' is not equal 4');
} else {
  console.log('You are wrong, ' +i+ ' is equal 4');
};
```

```javascript
// If X is not equal or more than X
var i = 3;
if(i != 4 || i < 4){
  console.log('Ummm, ' +i+ ' is not equal 4 or it is more than 4');
} else {
  console.log('Ummm, ' +i+ ' is equal 4');
};
```

### switch case
**Matching the expression's value to a case clause, and executes statements associated with that case.**

```javascript
var cars = 'audi';
switch(cars){
   case 'audi':
     console.log('It is A4');
	 break;
	 case 'ford':
     console.log('It is my car Ford');
	 break;
	 case 'ferrari':
     console.log('It is the slow car of Fernando Alonso');
	 break;
}
```

## Objects

### Simple Object
```javascript
var person = {
  name: 'mike',
	age: 20,
}
console.log(person.name);
```

Simple Object with Array

```javascript
var person = {
  name: 'mike',
	age: 20,
	daughters: ['Linda', 'Maggie'],
}
console.log(person.daughters[1]);
```

### Complex Object

Object with other object inside

```javascript
var person = {
  name: 'mike',
	age: 20,
	address: {
	   street: 'Velazquez 10',
		 city: 'Madrid'
	}
}
console.log(person.address.city);
```


# Tips

**JQUERY: Multiple CSS()**

```javascript
$selector.css({
   'font-size' : '10px',
   'width' : '30px',
   'height' : '10px'
});
```


**JS: default value to an undefined parameter**

```javascript
function functionWithDefaultValue(b){
    b = b || 123;
    return b;
}

// Result without parameter -----> Result 123
functionWithDefaultValue()   
// Result with parameter    -----> Result 66
functionWithDefaultValue(66) 

```


**JS: Return multiple values from a function**

```javascript
function operation(val1, val2){
	sum = val1 + val2;
	sub = val1 - val2;
	return {
		sum: sum, 
		sub: sub
	}; 
};
console.log( operation(20,5).sum ); // 25
console.log( operation(20,5).sub ); // 15


```
