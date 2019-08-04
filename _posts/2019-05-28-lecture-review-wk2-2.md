---
layout: post
title:  "Scope & Hoisting"
date:   2019-05-28
excerpt: "few important concepts to remember in scope and hoisting in Javascript"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ Javascript ]
---

---
### Scope #1
---
~~~javascript
function foo (){
  hi = 1;
}
foo();
~~~
Above variable hi will be automatically declared as a global variable and its corresponding value will be assigned if the declaration of the variable is not found anywhere in the current scope and in the global scope.  

---
### Scope #2
--- 
~~~javascript
function foo (){
    hi = 1; 
    /* 
    var keyword has not been used anywhere before, so this will  
    be automatically declared as a global variable in global scope.
    */
    function bar (){
        var hi = 3; 
        /* 
        var keyword has been used to declare so 'hi', so  
        'hi = 3' is limited to bar function scope.       
        */ 
        console.log(hi); // 3
    }
    bar();
}
foo();
console.log(hi); // 1
~~~ 
---
### Scope #3
---
~~~javascript
var randomNumber = 942;
console.log(window.randomNumber); // 942
~~~  
Global variables exist as "window" object's property as shown above.  

--- 
### Immediately Invoked Function (IIFE)
---
~~~
(function (para,meter){
    var varX = '1';
    var varY = '2';
    console.log(para);
    console.log(meter);
    console.log(varX + varY);
})();
~~~
The function should be wrapped inside a pair of round brackets and followed by a pair of around brackets (execution) in order to create a IIFE. If the function is not wrapped around a pair of round brackets, it will generate an error.

---
### Hoisting #1
---
~~~javascript
console.log(crepeFlavor); // undefined
var crepeFlavor = 'vanilla';
console.log(crepeFlavor); // 'vanilla'

makeCrepes(); // 'Here are some crepes for you!'

function makeCrepes() { // function written in function declaration
    console.log('Here are some crepes for you!');
}

makeOJs(); // error: makeOJ's is not a function. 
           // var makeOJs's declaration has been hoisted to the top 
           // but not its assigned values. var makeOJs = undefined;

var makeOJs = function() { // function written in function expression
    console.log('Here\'s a glass of fresh orange juice for you!');
}

makeOJs(); // 'Here's a glass of fresh orange juice for you!'
~~~
Variables and functions can be hoisted to the very top of the script. It is important to remember that only variable 'declarations' are hoisted, not the assigned values. Also, functions written in function declaration are hoisted to the top of the script, not the function expression functions.

---
### Hoisting Quiz 1
---
~~~javascript
var me = 'imho';
function foo() {
    console.log(me); // ?
    var me = 'someone else';
}
foo();
~~~
what can we expect in console? This can be a bit tricky at first time. The answer is undefined. var me is declared and assigned in the global scope first. Then function foo is executed. Inside foo function scope, console.log(me) is executed. It will look for any variable me declared inside the foo function scope. We have one var me variable declared and is hoisted to the top but not with its assigned value 'someone else'. Therefore, the var me's value is set as undefined and it is what is printed in the console. 

---
### Hoisting Quiz 2
---
~~~javascript
var me = 'imho';
foo();
var foo = function() {
    alert(me);
    var me = 'someone else';
};
~~~
First of all, functions written in function expressions are not hoisted to the top of the script, and only variable declarations are hoisted to the top. var foo is hoisted to the top and before it is assigned with a function, it is called on to execute as if it is a function. This will result in error that foo is not a function. 

---
### Hoisting Quiz 3
---
~~~javascript
function foo() {
    return 
    {
        age : 30
    };
}
console.log(typeof foo());
~~~
The answer is not object. The answer is undefined. This is because there should not be a new line after return statement. It should at least have a curly bracket in the same line in order to return as originally intended.

---
### JS Quiz 1
---
~~~javascript
console.log((true + false) > 2 + true) // ?
~~~
The answer is false. Think in terms of true and false as 1 and 0.. The + operator and - operators change booleans into numbers. Voila!

---
### JS Quiz 2
---
~~~javascript
var arr = ['hello','world'];
arr[2] = 'thank you';
console.log('2' in arr); // ?
~~~
The definition of 'in' operator from MDN: 
>The in operator returns true if the specified property is in the specified object or its prototype chain.  

Arrays implicity own properties as its corresponding index.

The answer is true.

---
### JS Quiz 3
---
~~~javascript
function foo() {
    var a = function (){
        console.log("expression");
    }
    a();
    function a(){
        console.log("yay");
    }
}
foo();
~~~

What will print in console? "yay" or "expression"? 
The answer is "expression". Inside the foo function scope, function written in function declaration is hoisted to the top of the function body, and then it is overwritten by the function written in function expression. Then the function a is executed. Therefore, the console will print "expression". 