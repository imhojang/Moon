---
layout: post
title:  "[Learning JS] ES2015 a.k.a ES6"
date:   2019-06-01
excerpt: "how to use let & const keyword, rest parameter & spread operator, and array & object destructuring"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
---
---
## let
---

In ES2015, new ways to declare a variable have been introduced. One of the ways is using the `let` keyword. Variables declared with `let` has some interesting features that makes it unique and different from variables declared with `var` keyword.  
1. block scope
2. temporal dead zone (TDZ)

---
## Block Scope
---

If a variable is said to have block scope, it means that the variable will not be accessible outside of its contained curly brackets { }.  

Take a look at a few examples demonstrating this:
~~~javascript
if (true) {
  let coffee = 'starbucks';
  var coffee2 = 'bluebottle';
}
function preference(type) {
  console.log ('my favorite coffee is from ' + type); 
}
preference(coffee);
preference(coffee2);
~~~
Here we have two variables declared inside a if, one declared with `var` and another declared with `let`.  
  
And there is a function that takes in an argument and clogs a message with the argument passed in.  
  
The function is executed two times, each with a different variable previously described. 

Intuitively, the following two lines will show up in console:
~~~javascript
'my favorite coffee is from starbucks'
'my favorite coffee is from bluebottle'
~~~
However, variable declared with `let` keyword has a block scope, therefore it will not be accessible outside of its container (curly brackets).

According to this, actually only one line will show up in console:
~~~javascript
'my favorite coffee is from starbucks'
~~~

Also, an error of something like the following will be generated:
~~~javascript
'Uncaught ReferenceError: coffee2 is not defined'
~~~

Here is another example demonstrating the scope of variables declared with `let`:

~~~javascript
let a = 1;
if (true){
    let a = 2;
    console.log(a); // 2
}
console.log(a) // 1
~~~

---
## Temporal Dead Zone (TDZ)
---
Definition of temporal dead zone from [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_dead_zone):
>**let** bindings are created at the top of the
(block) scope containing the declaration, commonly referred to as 
"hoisting". Unlike variables declared with `var`, which will start with the value `undefined`, `let` variables are *not* initialized until their definition is evaluated. Accessing the variable before the initialization results in a `ReferenceError`. The variable is in a "temporal dead zone" from the start of the block until the initialization is processed.

Take a look at this example: 
~~~javascript
function doSomething() {
    console.log(bar); // undefined
    console.log(foo); // ReferenceError : cannot access foo before initialization
    var bar = 1;
    let foo = 2;
}

doSomething();
~~~

Variable declared with `let` keyword **does get hoisted** but is **not accessible before initialization.**

Note the difference between this and hoisting variable declared with `var` keyword.

This is called "temporal dead zone".

---
## Const
---

Variables declared with `const` behaves similarlly to those declared with `let`, with an unique additional feature..

1. `const` variables also have block scope.
2. `const` variables also have temporal dead zone.
3. **`const` variables do not allow re-assignment of values**

The following example demonstrates the additional feature of `const`:

~~~javascript
const obj = {
    arr: [1,2,3];
};

obj = []; // does not work since it is assigning it to a different value 
obj.arr.length = 0; // works fine
obj.arr.push(1); //  works fine
~~~

Keep in mind that re-assignment is **different** from manipulation. 

The values can be manipulated using the appropriate methods. This is manipulation of the values in the object and is allowed with `const` variable.

However, assigning `const` variable to another value after its initial declaration & assignment will throw the following error:
~~~javascript
TypeError: invalid assignment to const `hi'
~~~

---
## Rest Parameter
---
~~~javascript
function foo (a,b, ...c) {
    console.log(c); // ['c','d','e','f']
    console.log(Array.isArray(c)); // true
}

foo('a','b','c','d','e','f');
~~~

`...c` creates a new array and puts the rest of the parameters inside the newly created array

~~~javascript

function foo2 (a,b, ...c) {
    console.log(arguments); // Arguments(5) [1,2,3,4,5, callee:(...),   
    Symbol(Symbol.iterator):f]
    console.log(Array.isArray(arguments)); //false
}

foo('1','2','3','4','5')
~~~

This example demonstrates the difference between array created from `arguments` keyword and those created from rest parameter. 

~~~javascript
function foo (...a, b) {
    console.log(a);
}

foo(1,2,3);
~~~

Rest parameter must be last parameter

---
## Spread Operator
---
~~~javascript
var arr1 = [ 1, 2, 3 ];
var arr2 = [ 4, 5, 6 ];

var total = [ ...arr1, ...arr2 ];

console.log(total); // [1,2,3,4,5,6]
~~~
Spread operator and rest parameter looks similar but it's function depends on where/how it is used.

~~~javascript
function foo (a,b,c){
    return a + b + c;
}

foo (...[ 1, 2, 3]); // rest parameter X spread operator O
~~~

Here in this example, '...' is being used as spread operator, not as rest parameter.

~~~javascript
var agentA = {
    codeName: 'oi',
    powerLevel: -999
};

var agentAA = {
    ...agentA
}
~~~

Not only arrays but also objects can be used with spread operator.

---
## Array & Object Destructuring
---

#### object destructuring

##### example 1
~~~javascript
var address = {
    city: 'new york',
    state: 'NY',
    zipcode: '10003'
};

var { city, state } = address;
// above is same as ...
// var city = address.city;
// var state = address.state;

console.log(city + ', ' + state);
~~~
##### example 2
~~~javascript
var address = {
    city: 'new york',
    state: 'NY',
    zipcode: '10003'
};

var { city: c, state: s } = address;

console.log(c + ', ' + s);
~~~

Makes a new variable with a different name. Then assigns the value in the object.

##### example 3
~~~javascript
var address = {
    city: 'new york',
    state: 'NY',
    zipcode: '10003'
};

function logAddress ({ city, state }) {
    console.log(city + ', ' + state);
}

logAddress(address);
~~~

#### Array destructuring

##### example 1
~~~javascript
var numbers = [ 1, 2, 3, 4, 5 ];

var [ one, two, three ,four, five ] = numbers;

console.log(one);
console.log(two);
~~~
##### example 2
~~~javascript
var numbers = [ 1, 2, 3, 4, 5 ];

var [ one, , , , five] = numbers;

console.log(one);
console.log(five);
~~~
##### example 3
~~~javascript
var numbers = [ 1, 2, 3, 4, 5 ];

function sum ([a,b,c,d,e]) {
    console.log(a+b+c+d+e);
}
sum (numbers);
~~~
##### example 4
~~~javascript
var numbers = [ 1, 2, 3, 4, 5 ];

function sum ([a,b, ...c]){
    console.log (c);
}

sum(number);
~~~
Rest parameter also works inside an array.

##### example 5
~~~javascript
cost guicheokPeople = [ 1, 2, 3, 4, 5 ];

function punish (...people) {
    console.log(people);
    const [ a, b, c, d, e ] = people;
    return c;
}

const result = punish(guicheokPeople);
~~~