# data-structure-algo-js-note
###### Notes related to LEARNING JAVASCRIPT DATA STRUCTURES AND ALGORITHM Book

#### Variables and Types in Javascript
> In JavaScript, the available types are numbers, strings, Booleans, functions, and objects. We also have undefined and
null, along with arrays, dates, and regular expressions.

```
var num = 1;
num = 3;
var price = 1.5;
var name = 'Packt';
var trueValue = true;
var nullVar = null;
var und;

console.log("num: "+ num);
console.log("name: "+ name);
console.log("trueValue: "+ trueValue);
console.log("price: "+ price);
console.log("nullVar: "+ nullVar);
console.log("und: "+ und);
```
> Output:
```
num: 3
name: Packt
trueValue: true
price: 1.5
nullVar: null
und: undefined
```
#### Variable Scope
```
var myVariable = 'global';
myOtherVariable = 'global';

function myFunction() {
  var myVariable = 'local';
  return myVariable;
}

function myOtherFunction() {
  myOtherVariable = 'local';
  return myOtherVariable;
}

console.log(myVariable);
console.log(myFunction());

console.log(myOtherVariable);
console.log(myOtherFunction());

console.log(myOtherVariable);
```
> Output:
```
global
local
global
local
global
```

#### Truthy and Falsy

| Value type | Result                                       |
| ---------- | -------------------------------------------- |
| undefined  | False                                        |
| null       | False                                        |
| Boolean    | true is true and false is false!             |
| Number     | (+0, -0, or NaN) is False ; otherwise True.  |
| String     | Length is 0 then False, Otherwise True       |
| Object     | True                                         |


#### '==' and '===' Confusions

###### For '==':
![Alt text](http://i.imgur.com/kaNMTus.png "Optional title")

###### For '===':
![Alt text](http://i.imgur.com/IgIovXL.png "Optional title")

#### Functions

> Function Arguments are variables with which a function is supposed to do something.

#### OOP
###### Object-oriented programming

> JavaScript objects are very simple collections of name-value pairs. There are two ways of creating a simple object in JavaScript. The first way is as follows:
```
var obj = new Object();
```
And the second way is as follows:
```
var obj = {};
```
In object-oriented programming (OOP), an object is an instance of a class. A class defines the characteristics of the object. This is how we can declare a class that represents a book:
```
function Book(title, pages, isbn){
this.title = title;
this.pages = pages;
this.isbn = isbn;
}
```
