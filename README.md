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
> In object-oriented programming (OOP), an object is an instance of a class. A class defines the characteristics of the object. This is how we can declare a class that represents a book:
```
function Book(title, pages, isbn){
this.title = title;
this.pages = pages;
this.isbn = isbn;
}
```
#### Array
> Declaring an array:
```
var numbers = [0,1,2,3,4,5,6,7,8,9];
var empty = [];
```
> Adding and removing elements

adds to the last
```
numbers.push(11,12);
```
adds to the first
```
numbers.unshift(-2);
numbers.unshift(-4, -3);
```
basically the operation does this:
```
for (var i=numbers.length; i>=0; i--){
numbers[i] = numbers[i-1];
}
numbers[0] = -1;
```
To remove a value from the end of an array, we can use the pop method:
```
numbers.pop();
```
To actually remove an element from the beginning of the array, we can use the shift
method as follows:
```
numbers.shift();
```
Manually to remove a value from the beginning of the array, we can use the following code:
```
var numbers = [1,2,4,5,6,7,8,9,0];

for (var i=0; i<numbers.length - 1; i++){
numbers[i] = numbers[i+1];
}

console.log(numbers);
```
We can use the splice method to remove an element from an array by simply
specifying the position/index we would like to delete from and how many
elements we would like to remove:
```
numbers.splice(5,3);
```
If we want to insert numbers 5 to 7 back into the array starting from
position 5. We can again use the splice method to do this:
```
numbers.splice(5,0,5,6,7);
```
###### Multi-Dimensional Array
```
var averageTemp = [];
averageTemp[0] = [72,75,79,79,81,81];
averageTemp[1] = [81,79,75,75,73,72];

console.log(averageTemp);
console.log("\n");

for (var i=0; i<averageTemp.length;i++){
  for (var j=0; j<averageTemp[i].length; j++){
    console.log(averageTemp[i][j]);
  }
}
```
Multidimensional Matrix
- Matrix 3x3x3 - Cube
```
var matrix3x3x3 = [];
for (var i=0; i<3; i++){
    matrix3x3x3[i] = [];
    for (var j=0; j<3; j++){
        matrix3x3x3[i][j] = [];
        for (var z=0; z<3; z++){
            matrix3x3x3[i][j][z] = i+j+z;
        }
    }
}

console.log(matrix3x3x3);

for (var i=0; i<matrix3x3x3.length; i++){
    for (var j=0; j<matrix3x3x3[i].length; j++){
        for (var z=0; z<matrix3x3x3[i][j].length; z++){
            console.log(matrix3x3x3[i][j][z]);
        }
    }
}
```
###### Array Methods:
![Alt text](http://i.imgur.com/ZdrvIKX.png "Optional title")

every and map:
```
var isEven = function (x) {
// returns true if x is a multiple of 2.
  console.log(x);
  return (x % 2 == 0) ? true : false;
};

var numbers = [2,0,4,5];

var myEvery = numbers.every(isEven);
var myMap = numbers.map(isEven);
console.log(myMap);
console.log(myEvery);
```
if we want to sum up all the values in an array, use reduce:
```
var numbers = [2,0,4,5];
var reduceResult = numbers.reduce(function(previous, current, index){
return previous + current + index;
});

console.log(reduceResult);
```
###### Sorting
```
var numbers = [2,0,4,5,6,8,9,3,1,7,10,11];

var reversed = numbers.reverse();
console.log(reversed);

var sorted = numbers.sort();
console.log(sorted);

//sort() can take a function as parameter if we need custom sorting rules
console.log(numbers.sort(function(a,b){
  return a-b;
}));

function compare(a, b) {
    if (a < b) {
        return -1;
    }
    if (a > b) {
        return 1;
    }
    // a must be equal to b
    return 0;
}

console.log(numbers.sort(compare));
```
> Understanding Javascript .sort parameter:

.sort takes an optional parameter, which should be a function.

.sort then calls that function repeatedly, passing it a pair of values from the array (the a and b parameters). The function then returns a value which is interpreted like so:

- If the returned value is less than 0, then a < b
- If the returned value is greater than 0, then a > b
- If the returned value is exactly 0, then a == b

Using this, .sort figures out the order of the items using whatever sorting algorithm the browser has been programmed to use.

In the absence of a sorting function, .sort will sort the items as strings - this is just an arbitrary point of the design. Ideally you should be passing a function to be used whenever you want to .sort things, as is the case here where the function forces the values to be compared as numbers.
