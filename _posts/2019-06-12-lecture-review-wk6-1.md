---
layout: post
title:  "DOM API II"
date:   2019-06-12
excerpt: " "
tag:
- javascript
- DOM
- event delegation
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ Javascript ]
---


```javascript
const $heading = document.createElement('h1');

$heading.textContent = 'Hello';

document.body.appendChild($heading);

const $ul = document.createElement('ul');

document.body.appendChild($ul);

const $li = document.createElement('li');
const $li2 = $li.cloneNode();

console.log($li2);

for (let i = 1; i < 6; i++) {
  $li.textContent = i;
  $ul.appendChild($li);

  // li element는 하나만 있음.
}
```

# mouseover vs mouseenter

## event delegation: 이벤트 위임 / 이벤트 캡쳐링 / 이벤트 버블링

## event bubbling

mouse over는 내부의 요소들이 달라지면 반복 **호출함**

## event capturing

mouse enter는 내부 요소들이 달라져도 반복 **호출하지 않음**

# data attribute \*dataset을 염두해 두기\*

```javascript
$0.innerHTML = '<h1 class="heading" data-title="babo">Hello</h1>';
$0.dataset.title; // "babo" - reading
$0.dataset.title = "chunjae" // writing
$0.dataset.title; // "chunjae" - reading
$0.innerHTML = '<h1 class="heading" data-abcabc="babu">Hello</h1>';
$0.dataset.abcabc; // "babu" reading
```

## dataset 은 어떤 객채든 존재하는 속성이다. 

> forEach method는 배열안의 요소의 숫자 만큼 괄호안의 함수를 실행한다. 

```javascript
const $tbody = document.querySelector('tbody');

DATA.forEach(function (data) {
  const $tr = document.createElement('tr');
  const $languageTd = document.createElement('td');
  const $percentageTd = document.createElement('td');

  $languageTd.textContent = data.language;
  $percentageTd.textContent = data.percentage;

  $tr.appendChild($languageTd);
  $tr.appendChild($percentageTd);
  
  $tr.dataset.id = data.id;

  $tr.addEventListener('click', function () {


    const language = $languageTd.textContent;
    alert(language);
    const languageData = DATA.filter(d => d.language === language)[0];
    const languageData = DATA.filter(d => d.id === $tr.dataset.id)[0];
    console.log(languageData);
  });
  // 만들면서 바로바로 이벤트를 넣어주는 것이 자연스러운 흐름이다.
  $tbody.appendChild($tr);
})
```

## textContent vs. innerHTML

둘다 모든 dom 객채에 존재. textContent가 더 먼저 표준화 되었기 때문에, 이것을 쓰는 것이 더 바람직하다.

## 만약 기준으로하는 정보가 여러개 일때를 대비하여, id 값을 만들어주어야한다. 

> 하지만 이때 id를 쓰는게 바람직한 것일까?  
> id를 쓰게되면 anchor이 생기는 것이고, 페이지에 하나만 있는 것이다.  
> id를 anchor로 사용하여 페이지 내의 이동이 있을때 url의 변화가 있다.  
> 이것은 꽤나 큰 변화로 간주된다.  
> 그렇기 때문에 여기서 dataset을 이용하여 id를 만들어주는 것이 적절하다.

- data set 이 나온 이유는 자바스크립트와 데이터를 분리해서 생각하도록 나온 것이다.
- data set 은 실무에서 쓸일이 많이 없다 왜냐하면 vue.js나 angular 같은 프레임워크에서
  대신처리해주기 때문이다.
- 하지만 dataset은 그 용도가 무궁무진하기 때문에 알아두는것이 좋다.
- 

## ***dataset 을 사용할 적절한 때를 잘 알아보자*** 

## debugger 을 꽂을 때, for 문이 시작되기 전에 꽂는 것이 더 유연하다

- 멈췄을때 다른 디버거들을 꽂기 편하다. 일일이 멈출 필요가 없다.
- 유연하게 사용할수있다.
- 버그가 나올때, 어느부분에서 버그가 나왔는지 정리가 확실히 되어야한다.
- reproduction step 을 알아야 다른 사람에게도 버그 발생한 경우를 전달할 수 있다.

