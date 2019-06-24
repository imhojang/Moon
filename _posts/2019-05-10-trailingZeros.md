---
layout: post
title:  "[Problem Solving] trailingZeros"
date:   2019-05-10
excerpt: "solving an algorithm called trailingZeros using JS"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
---

### 꼬리에 붙은 0 (trailingZeros)
--- 
###### 문제 이해 :
  * **Arguments**  
  (1) n : a positive integer  
  * **Conditions**  
  (1)  take the factorial of the integer n  
  (2)  find the number of trailing consecutive zeros
  * **Return**  
  (1) return the number of trailing zeros

###### 해결 방법 :  

* **Create a for loop** to calculate the factorial of the number
* **Convert the result** to into an array
* **Loop the array** from the end and count the number of consecutive zeros  

###### 코드 구현 :  
  ```javascript
  function trailingZeros(n) {
    var factResult = 1;
    for (var i = n; i > 1; i--) {
      factResult *= i;
    }
    var factArray = (`${factResult}`).split('');
    var zeros = 0;
    for (var b = factArray.length; factArray[b] === '0'; b--){
      if (factArray[b] === 0) {
        zeros++;
      }
    }
    return zeros;
  }
  ``` 

###### 결과 분석 : 
  * **test case 2 failed** "expected 9.332621544394418e+157 to deeply equal 24"  
    * In JS, large numbers above certain size is converted to scientific notation
  * **test case 3 failed** "expected infinity to deeply equal 91854977"  
    * In JS, numbers that are too large in size are converted to 'infinity'
  * **test case 4 failed** "expected infinity to deeply equal 748"  
    * Same as above
    

###### 해결 방법 : 
  * **Avoid factorial calculation** This is the core of the problem. So there must be another way to find the number of trailing zeros of a factorial of an integer without actually running the factorial.
  * **Find the pattern** 5! to 9! has one trailng zero, 10! to 14! has two, 15! to 19! has three, and 20! to 24! has four. The number of trailing zeros increments by one each time the number is greater than the next multiple of five.
    * However, at 25! to 29! has six trailng zeros instead of five zeros. Also, at 125! the number of trailing zeros increments by three.  
    * In conclusion, the number of trailing zeros of a number equals sum of the number divided by five, and the number divided by square of five, and the number divided by five to the third power, and so on.

###### 코드 구현 : 
```javascript
function trailingZeros(n) {
  var zeros = 0;
  var timesFive = 5;

  while (timesFive < n) {
    zeros += Math.floor(n / timesFive);
    timesFive *= 5;
  }
  return zeros;
}
```
#### 결과 분석 : 

  * **All tests passed !** 

  ![djokawari](djokawari.jpg "dj okawari's album art")