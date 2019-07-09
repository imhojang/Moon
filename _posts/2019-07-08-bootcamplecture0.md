---
layout: post
title:  "[Data Structure 0] Introduction to Stack, Queue, and LinkedList"
date:   2019-07-08
excerpt: " "
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
feature: https://images.unsplash.com/photo-1552550049-db097c9480d1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1234&q=80
---

# Data Structures (자료구조)

## Stack, Queue, and Linked list

프런트엔드에선 자료를 다룰 일이 많고, 언젠가는 자료구조를 알고 있어야할 상황을 마주할 것이기 때문에 이 개념들을 명확히 알고 있어야한다.

+ stack 이나 queue, 그리고 linkedlist는 언어에 국한되지 않고 효율을 보장할 수 있는 자료구조이다.

### Stack 

![alt](https://www.tutorialspoint.com/data_structures_algorithms/images/stack_representation.jpg)  
스택에는 여러 오퍼레이션이 있는데, 그 중에 push 라는 것이 있다.  
push를 하게 되면, 스택에 자료를 추가하는 것이다. 예를 들면 책을 쌓는 것과 비슷하게 생각해보면 된다.

그리고 pop이라는 것이 있는데, 이것은 스택의 자료를 제거하는 것이다.  
여기서 중요한게, pop를 하게 되면 가장 마지막에 추가된 자료 순서부터 제거한다.  
아까처럼 책으로 예를 들면, 가장 위에 있는 책부터 빼는 것과 같다고 보면 된다.

>이 개념을 LIFO, Last-In First-Out 이라고 할 수 있다.

#### Big O 

+ Insertion (삽입): O(1)
  + read as "oh-one"
  + 1: constant
  + 항상 동일한 오퍼레이션이 이루어지기 때문에 항상 시간적으로 O(1)이다.
+ Deletion (제거): **O(1)**
+ Search: O(n)
  + 여기서 n 은 스택의 사이즈를 가리킨다.
  + 찾고있는 자료가 맨 처음 혹은 맨 끝에 있을 수 있는 가능성이 있다.
  + 이 말은 즉 스택 하나하나를 다 봐야하는 것과 같다고 보기 때문에 O(n) 이라고 한다.

#### Real Life Use Cases

+ undo/redo mechanism
+ backwards/frowards mechanism of browsers
+ call stack

### Queue (줄)

![alt](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Data_Queue.svg/1200px-Data_Queue.svg.png)

+ Enqueue - 줄에 추가됨 (차례차례 추가됨)
+ Dequeue - 줄에서 빠짐 (앞에서 부터, 추가된 순서로 빠짐)

>"First-In First-Out" (FIFO) 
> => Queue 에서는 가장 먼저 추가된 자료가 가장 먼저 나올 수 있다.

#### Big O

+ Insertion: O(1)
+ Deletion: **O(1)**  
  + 설령 제거 대상이 중간에 끼어있다면? O는 무슨 값일까?
  + **찾는 시간은 제외해서 생각해야한다.**
  + 그러므로 **제거되는 것만 독립적으로 생각해보면** O(1)이다.
+ Search: O(n)

#### Real Life Use Cases

+ Line of people standing for food
+ Callback queue
  + 어떤 함수들이 줄을 서있는 것과 같은 구조. 앞에 있는 함수부터 차례차례 뺴와서 실행을 시킴.

### Linked list (연결 리스트)

![alt](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/Linkedlist.png)

+ LinkedList is made of a bunch of nodes that point to the next one in the list  
+ 연결리스트의 각각의 자료는 그 다음 자료에 대한 정보를 가지고 있다.
+ 연결리스트의 마지막 부분은 tail (꼬리)라고 한다.
+ 연결리스트의 맨 처음은 head (머리)라고 한다.
+ 배열과는 다르다.
+ 배열은 다음 item에 대한 정보가 없다.

#### Big O

+ Insertion: O(1)
  + 항상 동일한 오퍼레이션을 따를 것이기 때문에 매번 동일한 시간이 걸릴 것임.
+ Deletion: **O(1)**  
+ Search: O(n)  
  + n => linkedlist 사이즈

#### Real Life Use Cases

+ line of people standing for food
+ the history section of web browsers


>자료구조를 살필 때 **Big O 의 Insertion Deletion 그리고 Search** 이 세가지를 **무조건** 고려해보는 것이 좋다.

