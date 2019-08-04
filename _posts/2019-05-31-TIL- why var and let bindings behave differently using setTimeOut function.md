---
layout: post
title:  "Why var and let bindings behave differently using setTimeout function"
date:   2019-05-31
excerpt: "this one was bugging me so I made a post about it"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
feature: https://images.unsplash.com/photo-1547782793-e1444139967a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ JavaScript ]
---

~~~javascript
function timeOut() {
  for(var i = 0; i < 6 ; i++){
    setTimeout(function() { 
        console.log('print i : ' + i);
    }, i * 1000);
  }
}
~~~
Here is a function that should clog (console.log) i from 0 to 5, as shown below: 
~~~javascript
'print i : 0'
'print i : 1'
'print i : 2'
'print i : 3'
'print i : 4'
'print i : 5'
~~~ 
However, it actually clogs this:
~~~javascript
'print i : 5'
'print i : 5'
'print i : 5'
'print i : 5'
'print i : 5'
'print i : 5'
~~~
At first, this was counterintuitive, but things made sense after some research. 
The short answer for why this is happening is because variable declared with `var` keyword has a **function scope**, and there's only **one shared binding** for each of the loop iteration. 
For example, imagine that the compiler does this inside the for loop :
~~~javascript
setTimeout(function (){ console.log('print i : ' + i ), 0 * 1000} );
// first iteration: clog value of i after 0 sec
setTimeout(function (){ console.log('print i : ' + i ), 1 * 1000} );
// second iteration: clog value of i after 1 sec
setTimeout(function (){ console.log('print i : ' + i ), 2 * 1000} );
// third iteration: clog value of i after 2 sec
setTimeout(function (){ console.log('print i : ' + i ), 3 * 1000} );
// fourth iteration: clog value of i after 3 sec
setTimeout(function (){ console.log('print i : ' + i ), 4 * 1000} );
// fifth iteration: clog value of i after 4 sec
setTimeout(function (){ console.log('print i : ' + i ), 5 * 1000} );
// sixth iteration: clog value of i after 5 sec
~~~
After these setTimeout callback functions have been made, the *variable `i`* will have the value of 5.  
> A callback function is a special function which is used in AJAX so that server can respond to the client when it is ready to send data to the client.

Then the each of the setTimeout callback functions will be executed, which in turn prints `print i : 5` five times.

The reason why variable `i` is not printing from 0 to 5 is because variables `i` in every setTimeout callback means the **same variable** that finally is equal to 5 after the loop iteration ends.  

The same variable `i` is in the callback function, because variables declared with `var` keyword has a function scope. 

The variable `i` is not bound to the each callback function, and that is why the increment in variable `i` seems to be independent from the actual clog. 

Here's another copy of the above example without `print i : ` in clog for the sake of convenience :

~~~javascript
function timeOut(){
  for(var i = 0 ; i < 6 ; i++){
    setTimeout(function(){ console.log(i); }, i * 1000);
  }
}
~~~

After understanding why the actual clog of `i` using `var` keyword is different from the expection, these questions followed up inside my head:
>"Why does the variable `i` do not get affected in the same way?"   
>"Why does it clog 0, 1, 2, 3, 4, 5 seconds after the execution of the function?"  
>"Shouldn't it clog each iteration after 6 seconds if it is consistent with the logic above?"

After giving some thought, I realized that setTimeout's first argument, `function { console.log(i);}`, behaves differently from the second argument, `i * 1000`.

The second argument takes the variable `i` at each iteration, but the first argument does not.  

This is because the execution of callback function is conserved until it times out (0 sec, 1 sec, 2 sec ... etc).

Below is a step by step explanation of execution in each loop iteration:
~~~javascript
var i = 0; // declare var i and set its value to 0.
0 < 6; // conditional statement to run function body or not. i is 0, so true.
setTimeout(function(){ console.log(i); }, 0 * 1000);
/* 
executes setTimeout function in the function body.
in another word, "after 0 * 1000msec, call this function(){ console.log.(i); }"

the variable i inside console.log is not yet applied,
because the loop iterations have a precedence over the call of callback functions, unless specified as immediately invoked function (IIFE).
*/
i++ // i = 1
1 < 6
setTimeout(function(){ console.log(i); }, 1 * 1000);
//repeats until var i reaches 5, and the callback functions execute.


function() { console.log(i); } // after 0 * 1000msec
// 5
function() { console.log(i); } // after 1 * 1000msec
// 5
function() { console.log(i); } // after 2 * 1000msec
// 5
function() { console.log(i); } // after 3 * 1000msec
// 5
function() { console.log(i); } // after 4 * 1000msec
// 5
function() { console.log(i); } // after 5 * 1000msec
// 5

/*
The variable i is now 5 and console.log(5) executes six times 
after corresponding time has passed.
*/ 
~~~

So, how is this different from using `let` keyword to declare a variable?

With `let`, the variable has a block scope, and when used inside a for loop, **there will be a binding for each iteration.** Every setTimeout callback refers to a **different variable**, each of which has a different value. The first one is 0, next one is 1, etc.

~~~javascript
function timeOut(){
  for(let i = 0; i < 6; i++){
    setTimeout(function(){ console.log(i); }, i * 1000);
  }
}
~~~

~~~javascript
function() { console.log(i); } // after 0 * 1000msec
// 0
function() { console.log(i); } // after 1 * 1000msec
// 1
function() { console.log(i); } // after 2 * 1000msec
// 2
function() { console.log(i); } // after 3 * 1000msec
// 3
function() { console.log(i); } // after 4 * 1000msec
// 4
function() { console.log(i); } // after 5 * 1000msec
// 5
~~~

`let` keyword was introduced in ES6 or ES2015, and before that IIFE (immediately invoked function) was used to produce the same result of binding a variable with different value for each iteration.

Take a look at the example below.
~~~javascript
function timeOut() {
  for(var i = 0 ; i < 6 ; i++){
    (function (i) {
        setTimeout(function(){console.log(i);}, i * 1000);
    }(i));    
  }
};
~~~

Using IIFE with `var` keyword produces identical effect of using `let` keyword.

