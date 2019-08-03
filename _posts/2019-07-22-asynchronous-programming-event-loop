---
layout: post
title:  "Asynchronous Programming & Event Loop"
date:   2019-07-22
excerpt: " "
tag:
- async
- event loop
comments: true
feature: https://images.unsplash.com/photo-1552550049-db097c9480d1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1234&q=80
category: [ Javascript ]
---

# Event Loop 

- Javascript is a Single Threaded language - only one call stack
- V8 engine - open source - anyone can make changes, contribute, and use it
- Call stack 
- Callback queue 
- Asynchronous (비동기) - 
- Web API - 

> All of above are **closely related to Event Loop**

## V8 Engine - JS runtime engine

- heap : memory / storage. objects are stored in heap // this is different from the heap from data structure
- stack 

> V8 engine is two parts => heap & stack

## Web APIs

- AJAX
- Events
- Timing

> Web API is provided by the browser

## Call stack

- 현재 실행되는 프로그램들이 stack 구조에 저장되는 것  
  - 함수가 함수 안에서 실행 되면 차례대로 call stack에 쌓이고, 마지막에 들어간 것부터 call stack에서 실행 되고 종료됨 (LIFO)
- 무한대로 함수가 호출 될 경우 maximum call stack exceed라는 에러가 뜸.
- 무한대가 아닌 경우에서 브라우저가 정한 용량을 넘어서도 에러가 뜸.

```JS
console.log(1);
setTimeout(function foo() {
  console.log(3);
}, 1000);
console.log(2);
```

- setTimeout () =>  setTimeout도 콜스택에서 실행되고 빠짐.
- callstack 에 쌓이고 빠지는 순서
  - c.log (1), setTimeout, clog (2), foo(), clog (3)

## Callback queue

- this is where 'functions' wait to be processed.
- `setTimeout`, `setInterval`, `document`, `window` 등은 순수한 자바스크립트 함수가 아니고 브라우저가 추가적으로 제공해주는 것
- `setTimeout`을 쓰게 되면 web api한테 부탁함.
- callback queue에 하나씩 순서대로 들어감

## Run to Complete

- Once the code starts running, it continues till the end: 자바스크립트 중요한 특징하나
- callstack에 다 비워지기 전까지는 아무런 일도 일어날 수 없음
- callstack이 다 비워지면 계속 체크하고 있던 event loop이 callback queue 에 기다리고 있는 함수를 stack에 넣어줌

```JS
console.log(1);

console.log(2);

setTimeout() (function () {
  console.log(4);

  setTimeout(function () {
    console.log(6);
  }, 1000);
   
  console.log(5);
}, 1000);

console.log(3);

```

### Does function foo below get executed exactly after 2 seconds?

```Javascript
setTimeout(function foo () {
  alert(1);
}, 2000);
```

setTimeout을 실행하고 나서부터 web api에서 2초를 셈. **2초가 끝나면 callback queue에 줄을 세움**. 그리고 난 뒤에 eventloop이 줄을 슨 순서대로 fifo call stack에 쌓임.

> the time specifies the threshold after which a provided callback may be executed rather than the exact time the callback gets executes

> setTimeout에 명시하는 숫자는 콜백 함수가 정확히 실행되는 시간을 의미하기보다는 콜백 함수가 실행되기까지 걸리는 한계치를 말한다

google event loop website => loupe.

## what would happen on the screen?

```JS
button.addEventListener('click', () => {
  el.style.display = 'none';
  el.style.display = 'block';
  el.style.display = 'none';
  el.style.display = 'block';
  el.style.display = 'none';
  el.style.display = 'block';
  el.style.display = 'none';
  el.style.display = 'block';
})
```

- 마지막에 있는 `el.style.display = 'block';`만 실행됨
- run to completion의 성질 때문에 저 함수 실행이 끝나야 화면에 보여지기 때문.

## Render queue

### DOM construction

Bytes -> Characters -> Tokens -> Nodes -> DOM

- DOM Tree + CSSOM Tree => Render Tree
- Render Tree에는 화면에 보여져야할 요소들만 추려서 트리구조로 형성을 하는 것임
- 이 단계가 끝나면 Layout이라는 것을 실행함.
- 그리고 Painting 단계
- 
- DOM 이나 CSS 중 하나가 바뀌면 Render Tree 만들고, Layout 단계, Painting 단계 순서대로 항상 render queue에 쌓임.

> browswer dev tools 에 performance tab을 가서 확인 가능

- Recalculate style => Render Tree 만들고
- Update Layer Tree => Layer 단계
- Paint => Paint 단계