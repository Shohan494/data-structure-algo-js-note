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
## Array
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
#### Sorting
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
(Source: Stack Overflow)

###### Sorting objects:
```
var friends = [
    {name: 'John', age: 30},
    {name: 'Ana', age: 20},
    {name: 'Chris', age: 25}
];

function comparePerson(a, b){
    if (a.age < b.age){
        return -1
    }
    if (a.age > b.age){
        return 1
    }
    return 0;
}

console.log(friends.sort(comparePerson));

var names =['Ana', 'ana', 'john', 'John'];
console.log(names.sort());

console.log(names.sort(function(a, b){
    if (a.toLowerCase() < b.toLowerCase()){
        return -1
    }
    if (a.toLowerCase() > b.toLowerCase()){
        return 1
    }
    return 0;
}));
```
For accented characters, we can use the localeCompare method as well:
```
var names2 = ['Maève', 'Maeve'];
console.log(names2.sort(function(a, b){
return a.localeCompare(b);
}));
```
And the output will be:
```
["Maeve", "Maève"]
```

#### Searching
Through indexOf and lastIndexOf we can get the postion of the value in an array:
```
console.log(numbers.indexOf(10));
console.log(numbers.indexOf(100));
numbers.push(10);
console.log(numbers.lastIndexOf(10));
console.log(numbers.lastIndexOf(100));
```
Outputting the array into a string
```
console.log(numbers.toString());
```
If we would like to separate the elements by a different separator, such as - , we can use the join method to do just that:
```
var numbersString = numbers.join('-');
console.log(numbersString);
```
The output will be as follows:
```
1-2-3-4-5-6-7-8-9-10-11-12-13-14-15-10
```
## Stacks
A stack is an ordered collection of items that follows the LIFO (short for Last In
First Out) principle. The addition of new items or the removal of existing items takes
place at the same end. The end of the stack is known as the top and the opposite is
known as the base. The newest elements are near the top, and the oldest elements
are near the base.

###### Creating a Stack:

First, we need a data structure that will store the elements of the stack. We can use
an array to do this:
```
var items = [];
```
Next, we need to declare the methods available for our stack:
- **push(element(s))** : This adds a new item (or several items) to the top of
the stack.
- **pop()** : This removes the top item from the stack. It also returns the removed
element.
- **peek()** : This returns the top element from the stack. The stack is not
modified (it does not remove the element; it only returns the element for
information purposes).
- **isEmpty()** : This returns true if the stack does not contain any elements
and false if the size of the stack is bigger than 0.
- **clear()** : This removes all the elements of the stack.
- **size()** : This returns how many elements the stack contains. It is similar
to the length property of an array.

> So, the complete class of a basic stack will be like:

```
function Stack() {
    let items = [];
    
    this.push = function(element){
        items.push(element);
    };
    this.pop = function(){
        return items.pop();
    };
    this.peek = function(){
        return items[items.length-1];
    };
    this.isEmpty = function(){
        return items.length == 0;
    };
    this.size = function(){
        return items.length;
    };
    this.clear = function(){
        items = [];
    };
    this.print = function(){
        console.log(items.toString());
        //as array
        //console.log(items.toString());
    };
    this.toString = function(){
        return items.toString();
    };
}
```
###### Using of the stack functions
```
var stack = new Stack();
console.log(stack.isEmpty()); //outputs true

stack.push(5);
stack.push(8);
console.log(stack.peek()); // outputs 8

stack.push(11);
console.log(stack.size()); // outputs 3
console.log(stack.isEmpty()); //outputs false

stack.push(15);

var pop1 = stack.pop();
var pop2 = stack.pop();

console.log('pop1', pop1 ); // 15
console.log('pop2', pop2 ); // 11

console.log(stack.size()); // outputs 2
stack.print(); // outputs [5, 8]
```
###### Decimal to binary problem
```
function divideBy2(decNumber) {

  var remStack = new Stack(),
    rem,
    binaryString = '';

  while (decNumber > 0) {
    rem = Math.floor(decNumber % 2);
    remStack.push(rem);
    decNumber = Math.floor(decNumber / 2);
  }

  while (!remStack.isEmpty()) {
    binaryString += remStack.pop().toString();
  }

  return binaryString;
}

console.log(divideBy2(10));
```

###### Decimal to any base problem

```
function Stack() {

  let items = [];

  this.push = function(element) {
    items.push(element);
  };

  this.pop = function() {
    return items.pop();
  };

  this.peek = function() {
    return items[items.length - 1];
  };

  this.isEmpty = function() {
    return items.length == 0;
  };

  this.size = function() {
    return items.length;
  };

  this.clear = function() {
    items = [];
  };

  this.print = function() {
    console.log(items.toString());
  };

  this.toString = function() {
    return items.toString();
  };
}

function baseConverter(decNumber, base) {

  var remStack = new Stack(),
    rem,
    baseString = '',
    digits = '0123456789ABCDEF';

  // continue to store the result each time in the array
  while (decNumber > 0) {
    console.log('decNumber', decNumber);
    console.log('OPERATION : rem = Math.floor(' + decNumber + ' % ' + base + ')');
    rem = Math.floor(decNumber % base);
    console.log('rem', rem);
    console.log('OPERATION : remStack.push(rem)');
    remStack.push(rem);

    console.log('OPERATION : decNumber: ' + decNumber + ' =' + ' Math.floor(' + decNumber + ' / ' + base + ')');
    decNumber = Math.floor(decNumber / base);

    console.log('\n')

  }

  // continue to poping the result each time of the array
  // and then adding the value to the baseString variable
  while (!remStack.isEmpty()) {
    baseString += digits[remStack.pop()];
    //console.log("pop", digits[remStack.pop()]);
    console.log('baseString', baseString);
  }
  return baseString;
}

baseConverter(255, 16);
```
###### For a better understanding:
```
Math.floor(11 % 16); // 11
Math.floor(11 / 16); // 0

digits = '0123456789ABCDEF';

// baseString += digits[remStack.pop()];
baseString = digits[11]; // 'B'
```
## Queues

A queue is an ordered collection of items that follows the FIFO (which stands for
First In First Out, also known as first-come first-served) principle. The addition of
new elements in a queue is at the tail and the removal is from the front. The newest
element added to the queue must wait at the end of the queue.

#### Creating a queue

First, we need a data structure that will store the elements of the queue. We can
use an array to do it, just like we used for the Stack class in the previous chapter
(you will notice the Queue and Stack class are very similar, just the principles for
adding and removing the elements are different):
```
var items = [];
```
Next, we need to declare the methods available for a queue:

- **enqueue(element(s)) :** This adds a new item (or several items) at the back
of the queue.
- **dequeue() :** This removes the first item from the queue (the item that is in
the front of the queue). It also returns the removed element.
- **front() :** This returns the first element from the queue, the first one added,
and the first one that will be removed from the queue. The queue is not
modified (it does not remove the element; it only returns the element for
information purposes—very similar to the peek method from the Stack
class).
- **isEmpty() :** This returns true if the queue does not contain any elements
and false if the queue is bigger than 0.
- **size() :** This returns how many elements the queue contains. It is similar
to the length property of the array.

###### Complete Queue Class
```
function Queue() {
  var items = [];
  this.enqueue = function(element) {
    items.push(element);
  };
  this.dequeue = function() {
    return items.shift();
  };
  this.front = function() {
    return items[0];
  };
  this.isEmpty = function() {
    return items.length == 0;
  };
  this.clear = function() {
    items = [];
  };
  this.size = function() {
    return items.length;
  };
  this.print = function() {
    console.log(items.toString());
  };
}
```
###### Priority Queue With A Better Understanding:
```
function PriorityQueue() {

  console.log('Inside Main PriorityQueue()');
  let items = [];

  function QueueElement(element, priority) { // {1}
    this.element = element;
    this.priority = priority;
  }

  this.enqueue = function(element, priority) {
    console.log('Inside Main PriorityQueue()->this.enqueue()');

    let queueElement = new QueueElement(element, priority);
    console.log('Setting up value of queueElement: ', queueElement);
    let added = false;
    console.log('added set to false by default');
    console.log('added: ', added);
    
    for (let i = 0; i < items.length; i++) {
      console.log('inside for loop, i = ' + i + ' items.length = ' + items.length );
      if (queueElement.priority < items[i].priority) { // {2}
        // splice method (starts from index 'i',
        // removes 0 items, adds queueElements
        console.log('inside if block, so queueElement.priority < items[i].priority == true');
        console.log('because queueElement.priority: ' + queueElement.priority + '< items[i].priority: ' + items[i].priority );        
        items.splice(i, 0, queueElement); // {3}
        console.log('splice method, added queueElement in the index: ', i );
        added = true;
        console.log('added set to true');
        console.log('added: ', added);
        break; // {4}
      }
    }

    console.log('checking added outside the loop again: ', added);

    if (!added) {
      console.log('inside !added');
      console.log('added', added );
      console.log('!added', !added );

      items.push(queueElement); //{5}
      console.log('normally pushed queueElement');
    }
  
  };

  this.dequeue = function() {
    return items.shift();
  };

  this.front = function() {
    return items[0];
  };

  this.isEmpty = function() {
    return items.length == 0;
  };

  this.size = function() {
    return items.length;
  };

  this.print = function() {
    for (let i = 0; i < items.length; i++) {
      //console.log(`${items[i].element}  - ${items[i].priority}`);
      console.log(items);
      console.log('\n');
    }
  };
}

let priorityQueue = new PriorityQueue();

console.log('priorityQueue.enqueue("John", 3)')
priorityQueue.enqueue("John", 3);
priorityQueue.print();
console.log('priorityQueue.enqueue("Jackass", 1)')
priorityQueue.enqueue("Jackass", 1);
priorityQueue.print();
console.log('priorityQueue.enqueue("Jack", 2)')
priorityQueue.enqueue("Jack", 2);
priorityQueue.print();
console.log('priorityQueue.enqueue("Jack Ma", 2)')
priorityQueue.enqueue("Jack Ma", 2);
priorityQueue.print();
console.log('priorityQueue.enqueue("Camila", 4)')
priorityQueue.enqueue("Camila", 4);
priorityQueue.print();
```
###### Hot Potato : Circle Queue
```
function Queue() {

    let items = [];

    this.enqueue = function(element){
        items.push(element);
    };

    this.dequeue = function(){
        return items.shift();
    };

    this.front = function(){
        return items[0];
    };

    this.isEmpty = function(){
        return items.length == 0;
    };

    this.clear = function(){
        items = [];
    };

    this.size = function(){
        return items.length;
    };

    this.print = function(){
        console.log(items.toString());
    };
}


function hotPotato (nameList, num){

    let queue = new Queue();

    for (let i=0; i<nameList.length; i++){
        queue.enqueue(nameList[i]);
        console.log('Added in items: ', nameList[i]);
    }

    console.log("Players have been added, Game Begins!!");
    console.log('\n');

    let eliminated = '';
    
    while (queue.size() > 1){
        console.log("\n");
        console.log("inside while block as queue.size(): " + queue.size() +" > 1");
        for (let i=0; i<num; i++){
        console.log("inside for block due to while. i = " + i );
        console.log("\n");
          queue.enqueue(queue.dequeue());
          console.log(queue.print());
          //console.log(queue.enqueue(queue.dequeue()));
        }
        eliminated = queue.dequeue();
        console.log(eliminated + ' was eliminated from the Hot Potato game.');
        console.log(queue.print());
    }
    
    return queue.dequeue();
}

let names = ['John','Jack','Camila','Ingrid','Carl'];
let winner = hotPotato(names, 7);
console.log('The winner is: ' + winner);
```
###### For a better understanding:
```
let items = [];

enqueue = function(element){
  return items.push(element);
};

dequeue = function(){
  return items.shift();
};

enqueue("1st");
enqueue("2nd");
enqueue("3rd");
enqueue("4th");
enqueue("5th");

dequeue();
//enqueue(dequeue());
//same as
items.push(items.shift());
// see what happens..
console.log(items);
```
