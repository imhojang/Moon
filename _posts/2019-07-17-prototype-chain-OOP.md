---
layout: post
title:  "Prototype Chain & OOP"
date:   2019-07-17
excerpt: " "
tag:
- prototype chain
- object oriented programming
comments: true
feature: https://images.unsplash.com/photo-1552550049-db097c9480d1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1234&q=80
category: [ Javascript ]
---

## Object Oriented Programming

OOP is a programming paradigm organized around objects rather than actions and logic.

쉬운 말로,
우리가 쓰기 편한 물건을 발명하는 것이라고 생각하면 된다.

어떤 물건을 발명할지는 발명가의 창의적인 아이디어에 달린 문제이다.

Objects can contain related data and code,
which represent information about the thing you are trying to model,
and functionality or behavior that you want it to have.

객체는 우리가 만들고자 하는 물건에 대한 정보나 기능 또는 행동들을 가질 수 있다.

------

## Encapsulation - 캡슐화

**객체를 사용하는 측에서 그 내부 정보들을 접근할 수 없도록 캡슐처럼 감싸주고 보호해주는 것을 말한다.**

어떤 것을 보호할지 노출시킬 지 그건 발명가에게 달린 문제이다.

**간단히 말해서 어떤 데이터를 숨기는 것.**

factory function을 즉시실행함수로 감싸서, 클로저형성



------

**즉시 실행함수 자체를 변수에 담으면서 closure을 형성하여 encapsulate 시킬 수 있다.**

------

## abstraction - 추상화

**시용자가 알 필요 없는 내용은 모르게 하는것.**

**우리가 만든 객체를 사용자가 쉽게 쓰도록 해주는 것**

------

생성자 함수로 만들어서 언제든지 추가해서 만들 수 있도록 한다.

------

객체를 리턴하는 함수는 factory function이라고 한다. 

Javascript Factory Functions vs Constructor Function vs Classes

In javascript any function can return an object, but when it is not a constructor function, it is called factory function

------

## Inheritance - 상속

Car.call(this, owner) => 상위 클래스에 있는 생성자 함수의 key 와 value를 이어받기 위해 쓰는 것.

ElectricCar.prototype = Object.create(Car.prototype) 

=> Car의 프로토타입의 프로퍼티를 프로토타입으로 하는 객체를 만들어서 Electric Car 의 프로토타입으로 할당.

Car.prototype.constructor => Car;

ElectricCar.prototype.constructor = ElectricCar; => 위에서 ElectricCar의 프로토타입에 Car의 프로토타입을 할당하면서 ElectricCar의 constructor은 Car을 가리키고 있기때문에, ElectricCar으로 재할당.

------

구글 드라이브에 있는 이 코드를 보고 이해해보기 !!

------

Abstraction, Encapsulation, Inheritance 

**위의 세가지는 누가 물어보면 설명할줄 알아야함.**



**SOLID principle** (객체 지향 설계시 가장 기본적인 5가지 원칙.)**, KISS, GRASP** 등등도 있음. 이것도 찾아보고 정리하기.

SOLID 

S - Single responsibility principle - 단일 책임 원칙 - 한클래스는 하나의 책임만 가져야한다.

O - Open/closed principle - 개방-폐쇄 원칙 - 소프트웨어 요소는 확장에는 열려있으나' 변경에는 닫혀있어야한다.

L - ...

I - ...

D - Dependency inversion principle 

