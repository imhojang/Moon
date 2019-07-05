---
layout: post
title:  "[Learning JS] ES2015 & this"
date:   2019-06-01
excerpt: "further review on ES2015 and this keyword"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
---
- default parameter
- string interpolation a.k.a template literals
- arrow functions
- this (4 types of function call)  


---

## Default Parameter 

> Default values for parameters can be assigned when declaring a function

##### example #1

```javascript
function logName (name = 'ken', age = 6, school = 'UCSD') {
    console.log(name);
}

logName();
logName('wan');
```

##### example #2

```javascript
function logNumber (num = 666) {
    console.log(num);
}

logNumber();
logNumber(100);
logNumber(0); 
```

##### example #3 

```javascript
function getNumber () {
    console.log('Getting number..');
    return 666;
}

function logNumber (num = getNumber()) {
    console.log(num);
}

logNumber(); // 'Getting number..', 666 
logNumber(1000);

logNumber(false); // false
logNumber(null); // null
logNumber(undefined); // 'Getting number..', 666
```

default parameters are passed into the function only if the argument passed in is undefined.

## String interpolation (template literals)

##### example #1

const s = 'ken';

" " double quotes

' ' single quote

\` ` back-tick mark

```javascript
function getName() {
    return 'imho'
}

console.log(`my name is ${s}`);
```

' ' and " " are used conventionally. \` ` is used in special occasions.

when template literal (\` `) is used, expressions in curly brackets are compiled. 

\`${getName() + getName()}` = > 'my name is imhoimho'

## Arrow functions

##### example #1 

```javascript
const fn = (a) => {
    console.log(a);
};
fn();
```

Arrow function is always written in function expression (함수표현식). Not function declaration (함수선언식).

-> :  thin arrow

=>  : fat arrow

##### example #2 

```javascript
const fn = a => {
    console.log(a);
};
```

when there is only one argument, parenthesis can be removed to simplify the arrow function

##### example #3

```javascript
const multiply = (a, b) => a * b;
```

when there is only one execution, curly brackets can be removed to simplify the arrow function.

```javascript
function foo () {
    console.log(arguments);
}
foo(1,2,3); // 

const fn = () => {
    console.log(arguments);
};
fn(); // 

-------------------------------------------------------------------------------------------
    
function foo() {
    console.log(this);
    
    const fn = () => {
        console.log(this);
    };
    
    fn()
}
foo(1, 2, 3);
```

>**Arrow functions do not have its own 'this', 'argument'.**  

>**All functions in Javascript has 'this' and 'argument' keyword and is always accessible.**

```javascript
const name = 'ni';

const obj = {
    name: 'ken',
    logName: () => {
        console.log(this.name);
        console.log(arguments);
    }
};

obj.logName(1,2,3);

// arrow functions do not have its own 'this', 'arguments'
// what is 'this'?
```

## this (4 types of function call)

>the value stored in 'this' keyword depends on the situation it is being called.  
there are 4 specific situations 'this' keyword can be used.  

>'this'의 값은 'this'를 사용하는 해당 함수를 "어떤 방식으로" 실행하느냐에 따라 결정됩니다.  
그리고 함수를 실행하는 방법엔 4가지가 있습니다.  
(this를 이용하는) 해당 함수를 이 4가지중 어떤 방식으로 실행하느냐에 다라 this의 값은 바뀝니다.


### regular function call

// 1-1 in non-strict mode

```javascript
function foo () {
    console.log(this); // 'this' === global object (브라우저상에선 window 객체)
}

foo ();
```

>**you can't just look at the function and figure out what 'this' is.**

// 1-2 : in strict mode

```javascript
'use strict';
var name = 'ken';

function foo () {
    console.log(this.name); // 'this' === undefined
}

foo();
```

>strict mode does a lot of things... about 50 things.  
**Do some research on strict mode!** : this maybe a interview question  
>1. When strict mode is on and regular function call is called, this will always be **undefined**.
>2. strict mode cannot be enabled on developer tools console  

// example #1

```javascript
var age = 100;;

function foo () {
    var age = 99;
    bar(age); // regular function call. non-strict mode. so 'this' is window 
}

function bar (age) {
	console.log(this.age); // 100
}

foo();
```

### Dot Notation

// example #1 

```javascript
var age = 100;

var ken = {
    age: 35,
    foo: function foo () {
        console.log(this.age); //35
    }
};
ken.foo(); // 
```

// example #2

```javascript
function foo () {
    console.log(this.age);
}
var age = 100;
var ken = {
    age: 36,
    foo: foo
];
var wan = {
    age: 32,
    foo: foo
}
ken.foo(); // 36
wan.foo(); // 32
var fn = ken.foo;
fn(); // 100
```

// example #3

```javascript
var age = 100;
var ken = {
    age: 34,
    foo: function bar () {
        console.log(this.age);
    }
};
var wan = {
    age: 31,
    foo: ken.foo
};
var foo = ken.foo;
ken.foo();
wan.foo();
foo();
```

### Function prototype.call , function.prototype.bind, function.prototype.apply explicit binding.

>all functions have Funcion.call(), apply(), bind() method.

```javascript
var age = 100;
function foo () {
    console.log(this.age);
}
var ken = {
    age: 35,
    log: foo
};

foo.call(ken);
foo.apply(ken);
foo.bind(ken);

(1) call foo function (2) set this as ken (3) console.log (ken.age);
```

```javascript
function foo (a,b,c) {}
    console.log(this.age);
    console.log(a+b+c);
}
const ken = { age: 123};
foo.call(ken, 1,2,3) 
// 123
// 6
foo.apply(ken, [1,2,3,4,5,6,7,8,9]);
// 123
// 6
foo.bind() 
// ??? research on my own!

```

### New Keyword 

>using new keyword with this automatically creates a return value. also, written return value will not be returned. 

it will always return this. 

```javascript
function foo () {
    var age = 100;
}

new foo () // foo {};

function foo () {
    var age = 100;
    return this;
}
//above is function is the same as top function.

```

```javascript
function foo () {
    var age = 100;
    return 200;
}
new foo () // foo {};
```

```javascript
function foo () {
    var age = 100;
    return { hahaha: 23232 };
}
new foo () // foo { hahaha:23232 }
```

```javascript
function foo () {
    this.age = 100;
}
new foo () // foo { age: 100 }
```

>this 가 실행되는 포인트들을 자세히 관찰하자   

```javascript
function programmer () {
    this.isSmart = false;
    this.upgrade = function (version) {
        this.isSmart = !!version;
        work();
    }
}

function work () {
    if (this.isSmart) { // 여기서의 this는 위의 programmer안에서 실행됨. regular function call로 실행됨. 그러므로 this는 window 이고, isSmart 속성을 만든적이 없기 때문에 undefined 임. 
        window.alert("I can do my work! I am smart!"); // ?
    }
}

var programmer = new programmer();
// THINK: what should happen?
programmer.upgrade(1.1);
```

>이 예제에서 this가 어떤 순서로 설정이 되는지 여러번 반복하자
