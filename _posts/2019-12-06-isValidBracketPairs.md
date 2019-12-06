---
layout: post
title: "[Problem Solving] Valid Parentheses (LeetCode-Easy)"
date: 2019-12-06
excerpt: ""
tag:
    - javascript
    - algorithm
    - brackets
    - LeetCode
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [Algorithms]
---

### Valid Parentheses (괄호 짝이 맞는지 확인하기)

---

##### Problem Description:

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['`, and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

> `'('`, `')'`, `'{'`, `'}'`, `'['`, and `']'`만으로 이루어진 문자열이 있을 때, input이 valid한지 확인하세요.  
> input이 valid한 경우는 다음 조건들이 모두 만족할 경우입니다.
>
> 1.  열린 괄호가 같은 타입의 괄호로 닫힐 경우
> 2.  열린 괄호가 올바른 순서로 닫힐 경우

Example 1:

```
Input: "()"
Ouput: true
```

Example 2:

```
Input: "(){}{}"
Ouput: true
```

Example 3:

```
Input: "(]"
Output: false
```

Example 4:

```
Input: "([)]"
Output: false
```

Example 5:

```
Input: "{[]}"
Output: true
```

##### Approach:

1. 열린 괄호가 있을 시 그에 맞는 닫는 괄호를 가진 괄호map을 만든다
2. 열린 괄호가 있을 때마다 닫는 괄호를 push 할 stack을 배열로 만든다.
3. input 문자열의 첫번째부터 마지막까지 loop 을 돌린다
4. 만약 열린괄호라면 stack 에 넣고 닫는 괄호라면 stack에 가장 마지막에 들어간 닫는 괄호가 같은지 비교한다
5. 닫는 괄호가 다르다면 false를 반환한다
6. loop이 끝난 후 stack의 길이가 0이라면 true를 반환, 아니라면 false를 반환
7. 문자열의 길이가 0일 경우 true를 반환하고 홀수 일 경우 바로 false 를 반환하는 로직을 최상단에 적는다

##### Code

```javascript
function isValid(s) {
    // 문자열 길이가 0 일 경우 true 반환
    // 문자열 길이가 홀 수 일 경우 false 반환
    if (!s.length) {
        return true;
    } else if (s.length % 2 !== 0) {
        return false;
    }

    // 괄호 맵
    const map = {
        "(": ")",
        "{": "}",
        "[": "]"
    };
    // 배열로 만든 스택
    const stack = [];

    // 문자열의 길이만큼 loop
    for (let i = 0; i < s.length; i++) {
        // 열린 괄호일 경우
        if (map.hasOwnProperty(s[i])) {
            // 스택에 닫힌 괄호 추가
            stack.push(map[s[i]]);

            // 닫힌 괄호일 경우 스택의 가장 최근에 들어간 괄호인지 비교하여
        } else if (stack.pop() !== s[i]) {
            // 다를 경우 false 반환
            return false;
        }
    }

    // loop 이 다 마치고 난 후 stack.length 가 0 인지 확인
    return stack.length === 0;
}
```
