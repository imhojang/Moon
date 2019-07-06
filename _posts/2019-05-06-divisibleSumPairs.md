---
layout: post
title:  "[Problem Solving] divisibleSumPairs"
date:   2019-05-06
excerpt: "my approach on divisibleSumPairs using JS"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
feature: https://images.unsplash.com/photo-1453733190371-0a9bedd82893?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1267&q=80

---

### 합해서 나눠떨어지는 쌍 찾기 (divisibleSumPairs)
---
###### 문제 이해 :
  *   **Arguments**  
  (1) array ar : an array of integers  
  (2) integer k : a positive integer  
  * **Conditions**  
  (1) when i < j,  
  (2) and ar[i] + ar[j] equal multiples of k,  
  (3) ar[i] and ar[j] are a valid pair
  * **Return**  
  (1) return the number of pairs that meet the condition above.

###### 해결 방법 :  
  * **Create a for loop** that loops through each item in the array (*declare index variable i*)
  * **Create a nested for loop** that always begins one index ahead of the outer loop and loops through rest of the item in the array (*declare index variable j*)
  * **Check if the sum of the integers** at ar[i] and ar[j] are divisible by the *argument integer k*
  * **Count** the number of times the sum of the pairs were multiples of k.  
  * on completion of the loop, **return the count of pairs**

###### 코드 구현 :  
  ```javascript
  function divisibleSumPairs(k,ar) {
      var pairCount = 0;
      for (var i = 0; i < ar.length; i++){
          for (var j = i + 1; j < ar.length ; j++) {
              if((ar[i] + ar[j]) % k === 0 ) { pairCount++; }
          }
      }
      return pairCount;
  }  
  ``` 

###### 결과 분석 :  
  * **All tests passed !**

    ![fireworks at lotte world tower on May 5th, 2019](/assets/postimg/fireworksatlotteworldtower.png "The fireworks at Lotte WT")