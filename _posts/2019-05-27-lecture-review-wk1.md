---
layout: post
title:  "Javascript Grammar"
date:   2019-05-27
excerpt: "fill in the blank & short answer questions written to review Javascript grammar"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ JavaScript ]
---

>Fill in the blank and answer the questions.  
>On completion, check your answers with the answers on the bottom of the page. 
---
### Questions

###### Value
    - What is it called in Korean?
    - Use  _______  to change the value.

###### Variable 
    - What is it called in Korean?
    - Creating this is like assigning _______ to a value.
    - Variable makes the assigned value _______ & _______.

###### Identifier
    - What is it called in Korean?
    - It indicates the _______ of an assigned variable.
    - (a),(b),(c) and (d) can be used to create an identifier.
    - Identifiers cannot start with _______.
    - Javascript _______ cannot be used as an identifer.

###### Naming Convention
    - Use _______case.
    - What is _______case?

###### Type
    - List 7 types of values in Javascript. 
      *hint: use the acronym 'bonus'*
    - Use _______ operator to find the type of a value.
---
#### Number
    - Number._______(1); // ? Number._______(0.1); // ?
    - What is the property of Number object that checks if a 
      number is a integer and returns boolean?

###### Handling Numbers 

    arithmetic operators
    - 14 % 3; // ? 
    - What is the name of % ?
    - 4 ** 3 // ? 
    - What is the nmae of ** ?

    comparison operators
    - What is the difference between == and === ?
    - 0 == false // ?
    - 0 === false // ?
    - 2 == '2' // ?
    - 2 === '2' // ?
    - == is known as t_______ c_______ operator
    - === is known as s_______ e_______ operator
    - one shouuld always use _______ operator for comparing 
      variables or just for any comparison
    - null == undefined // ?
    - null === undefined // ?
    - NaN === NaN // ?
    - Remember that NaN is _______ _______ _______ _______,
     including _______.

    increment/decrement operators
    - What is the difference between --a and a-- (or ++a and a++)?
    - Both increments/decrements the variable. 
      However, returns different values.
    - When a = 1, ++a returns _______.
    - When a = 1, a++ returns _______.
    - Think in terms of the order of the operator & value.
    - In any case, follow the guideline "prefer ++a over a++".

    assignment operators 
    - +=, -=, *=, /=, %=, **=

###### Operator precedence
    - associativity 
    - left associativity = _______ to _______.
    - right associativity = _______ to _______.

    example of right associativity: the assignment operators
    - a = b = 5 // order of assignment ?

    - Which operator has a higher operator precedence? && or ||?


###### Special Numbers
    - _______, _______, _______, _______.

###### NaN
    - What does it stand for?
    - What type is NaN?
    - NaN === NaN; // ?
    - 0 / 0; // ?
    - 1 * 'hello'; // ?

###### parseInt, parseFloat
    - parseInt('123'); // ?
    - parseInt('110',2); // ?
    - parseFloat('12.345'); // ?
    - parseInt('hello'); // ?

    - What does parseInt() & parseFloat() do?

---
#### String

###### Writing strings
    - What are the three different ways of writing strings?
    - What is the name of ` ` and its function?

###### Handling strings 
    - 'a' < 'b'; // ?
    - 'abc' > 'aaa'; // ?
    - 'a' , 'z'; // ?
    - '한글' < '한국어'; // ?
    - '2' < '10'; // ?

###### Characteristics 
    - 'hello'[3] // ?
    - 'hello'.concat('fun','javascript'); // ?
    - '6'.repeat(3); // ?
    - 'hello javascript'.includes('hello'); // ?
    - 'hello javascript'.startsWith('he'); // ?
    - 'hello javascript'.endsWith('ript'); // ?
    - 'hello javascript'.indexOf('java'); // ?
    - 'hello'.slice(2,4); // ?
    - '    hello    '.trim(); // ?
    - 'hello!fun!javascript'.split(!); // ?

###### Strings are immutable
    var a = 'hello';
    a[3] = '0';
    console.log(a); // ?

---
#### Boolean
    - The only boolean values are _______ and _______.

###### Converting to Boolean values
    - !!'hi'; // ?
    - Boolean('hi'); // ?

###### Truthy & Falsey
    - In Javascript, all values are truthy but for these 8 values:
      *hint: 3 number types 2 string types 1 boolean type + 2 more.*
---
#### null & undefined
    - What are their differences?
    - As a programmar one should use _______ in order to indicate
      that the value does not exist.

    - typeof null; // ? *hint: not null type*
--- 
#### Function
    function add(x,y){return x+y;}
                 (a)   (b)
    - What is (a)? and what is it called in Korean?
    - What are the two main functions of (b)?  


###### arguments keyword in a function
    function foo(x,y){
        console.log(arguments);
    }
    foo(1,2); // ? *hint: [object Arguments]{   ?   }*

    - can use arguments.length
    - however, object.length returns undefined => instead use
      Object.keys(myObj).length
    - This is because arguments keyword has its own property 
      called length, but object does not.
--- 
#### Control flow
    function add(x,y){ return function bar(){}; }

    - add() || 3 // ?
    - add()() || 3 // ?

###### Switch
    - What are the 4 keywords when using switch? 
    - write an example of using switch.

###### Break, Continue
    - What are their functions in association with a loop?
      break: ex_______ loop, moves to next code.
      continue: sk_______ the rest oft he code in the loop.

###### for loop
    for( init() ; isValid() ; console.log(3) ) { return 3; }

    - Write the order of each expression executed from the for
      loop above.
--- 
#### Objects

###### Dot notation & Bracket Notation
    - What are these and what is the specific case bracket 
      notation must be used?

###### Handling Objects
    var person;

    //Adding
    person.name = 'Imho Jang'
    person.age = '25';
    person.languages = ['Korean','English'];

    //Writing
    person.age = '26';
    
    //Reading
    person.name; // ?
    perosn.age; // ?

    //Deleting
    delete person.name;

    //Checking
    'name' in person; // ?
    'phone number' in person; // ?

###### Method
    - A function can be assigned as the value of a property
      in an object. This is called a method.
    - Write a sample method.
---
#### Array
    - typeof []; // ?
    - A main difference between object and array is that 
      items in array has an _______.
    - Each value in an array are called _______ or _______. 
      What is it in Korean?

--- 
### Answers

###### Value
    - What is it called in Korean? 값
    - Use OPEARTOR to change the value.

###### Variable 
    - What is it called in Korean? 변수
    - Creating this is like assigning NAME to a value.
    - Variable makes the assigned value USABLE & REUSABLE.

###### Identifier
    - What is it called in Korean? 식별자
    - It indicates the NAME of an assigned variable.
    - ALPHABET, NUMBER, DOLLAR SIGN $ and UNDERSCORE _ can be 
      used to create an identifier.
    - Identifiers cannot start with NUMBER.
    - Javascript KEYWORDS cannot be used as an identifer.

###### Naming Convention
    - Use CAMELcase.
    - What is CAMELcase? -> cookiesAndCream; icedAmericano, bakedPotato

###### Type
    - List 7 types of values in Javascript.  
      *hint: use the acronym 'bonus'*
      BOOLEAN OBJECT NUMBER NULL UNDEFINED STRING SYMBOL
    - Use 'typeof' operator to find the type of a value.
---
#### Number
    - Number.IsIntegre(1); // ? Number.IsInteger(0.1); // ?

###### Handling Numbers 

    arithmetic operators
    - 14 % 3; // ? 2 
    - What is the name of % ? MOD OPERATOR
    - 4 ** 3 // ? 4*4*4 = 64
    - What is the nmae of ** ? EXPONENTIATION OPERATOR

    comparison operators
    - What is the difference between == and === ? == IS FLEXIBLE
      IN CHECKING EQUALITY WHILE === IS STRICT
    - 0 == false // ? TRUE
    - 0 === false // ? FALSE
    - 2 == '2' // ? TRUE
    - 2 === '2' // ? FALSE
    - == is known as tYPE cOERCION operator
    - === is known as sTRICT eQUALITY operator
    - one shouuld always use STRICT EQUALITY operator for comparing
      variables or just for any comparison
    - null == undefined // TRUE
    - null === undefined // FALSE
    - NaN === NaN // FALSE
    - Remember that NaN is NOT EQUAL TO ANYTHING, including ITSELF.

    increment/decrement operators
    - What is the difference between --a and a-- (or ++a and a++)?
      THEY ARE DIFFERENT IN TERMS OF RETURN VALUES. 
    - Both increments/decrements the variable. However, returns 
      different values.
    - When a = 1, ++a returns 2.
    - When a = 1, a++ returns 1.
    - Think in terms of the order of the operator & value.
    - In any case, follow the guideline "prefer ++a over a++".

    assignment operators 
    - +=, -=, *=, /=, %=, **=

###### Operator precedence
    - associativity 
    - left associativity = LEFT to RIGHT.
    - right associativity = RIGHT to LEFT.

    example of right associativity: the assignment operators
    - a = b = 5 // order of assignment ? (1) b = 5 (2) a = b 

    - Which operator has a higher operator precedence? && or ||? &&


###### Special Numbers
    - NaN, -0, -infinity, +infinity

###### NaN
    - What does it stand for? NOT A NUMBER
    - What type is NaN? NUMBER
    - NaN === NaN; // FALSE
    - 0 / 0; // ? NaN
    - 1 * 'hello'; // ? NaN

###### parseInt, parseFloat
    - parseInt('123'); // 123
    - parseInt('110', 2); // 6 -> parses integer into binary number
    - parseFloat('12.345'); // 12.345
    - parseInt('hello'); // NaN

    - What does parseInt() & parseFloat() do? PARSES A NUMBER IN 
      STRING INTO INTEGER OR DECIMAL

---
#### String

###### Writing strings
    - What are the three different ways of writing strings? ``, '', and ""
    - What is the name of ` ` and its function? TEMPLATE LITERAL

###### Handling strings 
    - 'a' < 'b'; // TRUE
    - 'abc' > 'aaa'; // TRUE
    - 'a' > 'z'; // FALSE
    - '한글' < '한국어'; // FALSE
    - '2' < '10'; // FALSE

###### Characteristics 
    - 'hello'[3] // ? 'l'
    - 'hello'.concat('fun','javascript'); // 'fun javsacript'
    - '6'.repeat(3); // ? '666'
    - 'hello javascript'.includes('hello'); // ? TRUE
    - 'hello javascript'.startsWith('he'); // ? TRUE
    - 'hello javascript'.endsWith('ript'); // ? TRUE
    - 'hello javascript'.indexOf('java'); // ? 6
    - 'hello'.slice(2,4); // ? 'll'
    - '    hello    '.trim(); // ? 'hello'
    - 'hello!fun!javascript'.split(!); // ? ['hello', 'fun', 'javascript'];

###### Strings are immutable
    var a = 'hello';
    a[3] = '0';
    console.log(a); // 'hello'

---
#### Boolean
    - The only boolean values are TRUE and FALSE.

###### Converting to Boolean values
    - !!'hi'; // ? TRUE
    - Boolean('hi'); // ? TRUE

###### Truthy & Falsey
    - In Javascript, all values are truthy but for these 8 values:
      *hint: 3 number types 2 string types 1 boolean type + 2 more.*
      (1) false, (2) NaN, (3) -0, (4) 0, (5) null, (6) undefined, (7) '', (8) "", 

#### null & undefined
    - What are their differences? 
    UNDEFINED IS USED TO INDICATE THAT A VALUE HAS NEVER BEEN ASSIGNED.
    NULL IS USED TO INDICATE THAT A VALUE DOES NOT EXIST.
    - As a programmar one should use NULL in order to indicate that 
      the value does not exist.

    - typeof null; // ? OBJECT *hint: not null type*

#### Function
    function add(x,y){return x+y;}
                 (a)   (b)
    - What is (a)? ARGUMENT and what is it called in Korean? 인자
    - What are the two main functions of (b)? IT IS THE CONCLUDING VALUE ON EXECUTION  
      OF THE FUNCTION AND IT ALSO TERMINATES THE FUNCTION. CODE BELOW RETURN LINE  
      INSIDE THE FUNCTION BODY WILL NOT BE READ.


###### arguments keyword in a function
    function foo(x,y){
        console.log(arguments);
    }
    foo(1,2); // ? *hint: [object Arguments]{ 0: 1, 1: 2  }*

    - can use arguments.length
    - however, object.length returns undefined => instead use Object.keys(myObj).length
    - This is because arguments keyword has its own property called length, but object does not.

#### Control flow
    function add(x,y){ return function bar(){}; }

    - add() || 3 // function bar()
    - add()() || 3 // 3

###### Switch
    - What are the 4 keywords when using switch? default, case, switch, break
    - write an example of using switch.
    
    function translateColor(english) {
      var result;
      switch (english) {
        case 'red':
        result = '빨강색';
        break;
        case 'blue':
        result = '파랑색';
        break;
        case 'purple':
        result = '보라색';
        break;
        case 'violet':
        result = '보라색';
        break;
        default:
        result = '일치하는 색깔이 없습니다.';
      }
      return result;
    }

###### Break, Continue
    - What are their functions in association with a loop?
      break: exITS loop, moves to next code.
      continue: skIPS the rest oft he code in the loop.

###### for loop
    for( init() ; isValid() ; console.log(3) ) { return 3; }

    - Write the order of each expression executed from the for loop above. 
      (1) init(), (2) isValid(), (3) return 3, (4) console.log(3)

#### Objects

###### Dot notation & Bracket Notation
    - What are these and what is the specific case bracket notation must be used? 
    WHEN THE PROPERTY NAME INCLUDES STRINGS THAT DOES NOT FOLLOW THE RULES USED
    TO CREATE IDENTIFIERS (ex) Strings that are not alphabet, number, $, or _.

###### Handling Objects
    var person;

    //Adding
    person.name = 'Imho Jang'
    person.age = '25';
    person.languages = ['Korean','English'];

    //Writing
    person.age = '26';
    
    //Reading
    person.name; // 'Imho Jang'
    perosn.age; // '25'

    //Deleting
    delete person.name;

    //Checking
    'name' in person; // TRUE
    'phone number' in person; // FALSE

###### Method
    - A function can be assigned as the value of a property in an object. This is called a method.
    - Write a sample method.
    var person = {  
      greet: function() {
        return 'hello';  
      }
    };
     
    person.greet(); // 'hello';


#### Array
    - typeof []; // object
    - A main difference between object and array is that items in array has an ORDER.
    - Each value in an array are called ITEM or ELEMENT. What is it in Korean? 항목 또는 요소
