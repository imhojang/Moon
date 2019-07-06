---
layout: post
title:  "[Learning JS] Object/Array & Primitive/Reference"
date:   2019-05-27
excerpt: "notes on object, array, primitive and reference data type in Javascript"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
feature: https://images.unsplash.com/photo-1472437774355-71ab6752b434?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1267&q=80

---

---
### Object 
---
###### example 1
    var obj = { name: 'imho' };
    for (var prop in obj) { console.log(prop) };

    <console>
    "name" 
    -> the properties in objects are in String type 
      (even when they are not in quotes) 
      On the other hand, the values in object can be just about
      anything. 
      e.g. function, string, object, array, nested object, etc.  

###### example 2
    var a = 'firstName';
    var obj = { a : 'imho'; };

    console.log(obj);

    <console>
    [object Object]{ firstName : 'imho' }

    => [object Object] shows up when an object is turned into a string. 
    This depends on the console environment. (e.g. jsbin vs. deveoper tool)

    ---------------------------------------------------------------------------
    
    accessing property-value-pair in objects.

    obj[a] == obj['firstName'] // undefined

    obj.a => looks for the property named "a"

##### Dot Notation vs Bracket Notation
    dot notation : objectName.propertyName

    bracket notation : objectName['propertyName'] or
                       objectName[propertyNameVariable]

    the variable used in bracket notation must be String
---
### Array
---
    It could be said that array is a subcategory of object.

    e.g. typeof [1, 2] // object
         typeof [] // object
    
    Array.push(1) returns the length property value of the new array.
    
    It is the same with Array.pop();

    e.g. var arr = [1,2,3]; 
         console.log( arr.push(4) ) // 4
    
---
### Primitive
---
    Boolean, number, string, null, and undefined are primitive types.

    Primitive values are immutable, meaning that they cannot be directly altered.
    This is different from the values being replaced/reassigned with a new value.


    // Using a string method doesn't mutate the string
    var bar = 'baz';
    console.log(bar); // baz
    bar.toUpperCase();
    console.log(bar); // baz
    console.log(bar.toUpperCase()) // baz

    // Using an array method mutates teh array
    var foo = [];
    console.log(foo); // []
    foo.push('plugh');
    console.log(foo); // ['plugh']

    // Assignment gives the primitive a new (not a mutated) value
    bar = bar.toUpperCase(); // BAZ

    ---------------------------------------------------------------------------

    var foo = 5;

    function addTwo(num) {
        num += 2;
    }

    function addTwo_v2(foo){
        foo += 2;
    }

    addTwo(foo);
    console.log(foo); // 5

    addTwo_v2(foo);
    console.log(foo); // 5

    The results are 5 not 7 because primitive values are immutable and 
    we are working on the copies of the original variable, not on the 
    original (external) foo's value. 
    In this situation, the external foo variable cannot be accessed in any way.

---
### Reference
---
    var arr = [1,2,3];
    var arr2 = arr;
    var arr3 = [1 ,2];

    /*
    Here both arr and arr2 are pointing at the same array object.
    Therefore, the change using arr2 variable will be reflected
    in arr variable as well.
    */

    arr2.pop();

    console.log(arr2) // [1, 2]

    console.log(arr) // [1, 2]

    arr === arr2 // true 
    arr2 === arr3 // false
    arr === arr3 /// false

    /* 
    arr and arr2 do not equal to arr3 although they appear to have
    the same values. This is because the array object in arr and arr2
    is a just an another array object with same values as the values in arr3.
    */
    
