---
layout: post
title:  "[Problem Solving] Climbing Stairs (LeetCode-Easy)"
date:   2019-12-06
excerpt: ""
tag:
- javascript
- algorithm
- LeetCode
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ Algorithms ]
---

### Climbing Stairs (계단오르기)
---

##### Problem Description:
You are climbing a stair case. It takes n steps to reach to the top.  
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?  

Note: Given n will be a positive integer

> 당신은 계단을 걷고 있고, 계단의 맨 위까지는 n 걸음이 걸립니다. 한번에 1 걸음이나 2걸음을 걸을 수 있다면 몇가지 걸음의 조합으로 맨 위까지 도달할 수 있을까요? 단 n은 양의 정수입니다.

Example 1:
```
Input: 2
Output: 2
Explanation: There are two ways to the top
1. 1 step + 2 step
2. 2 steps
```

Example 2:
```
Input: 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

###### Approach

일단 패턴을 분석해보았다
1. n = 1 일때는 1가지
- (1) 1
2. n = 2 일때는 2가지
- (1) 1 + 1, (2) 2
3. n = 3 일때는 3가지
- (1) 1 + 1 + 1, (2) 1 + 2, (3) 2 + 1
4. n = 4 일때는 5가지
- (1) 1 + 1 + 1 + 1, (2) 2 + 2, (3) 1 + 1 + 2, (4) 1 + 2 + 1, (5) 2 + 1 + 1 
5. n = 5 일때는 8가지
- (1) 1 + 1 + 1 + 1 + 1, (2) 2 + 2 + 1, (3) 2 + 1 + 2, (4) 1 + 2 + 2, (5) 1 + 1 + 1 + 2, (6) 1 + 1 + 2 + 1, (7) 1 + 2 + 1 + 1, (8) 2 + 1 + 1 + 1  

6. continues...

패턴을 보아하니, n이 3일때부터 그 전 두 스텝의 가지 수를 더한 값이다.
  
n = 3 -> 1 + 2 = 3가지

n = 4 -> 2 + 3 = 5가지

n = 5 -> 3 + 5 = 8가지

패턴을 분석했으니 이제 코드로 적어보겠다

##### Code

```
var climbStairs = function(n) {
  
  // n이 2보다 작거나 같은 경우 n 값과 가지수가 동일하므로 그대로 반환한다.
  if (n<=2) {
    return n
   }
 
  var fn;
  var f1 = 1;
  var f2 = 2;
  
  // 3도 가지수가 동일하지만 패턴이 시작되므로 3부터 n 까지 loop을 돈다
  for (let i = 3; i <= n; i++) {
    // fn은 더한 값
    fn = f1 + f2
    // f1 을 f2로 업데이트한다
    f1 = f2;
    // f2 를 더한 값으로 업데이트한다
    f2 = fn;
  }

  return fn
};
```