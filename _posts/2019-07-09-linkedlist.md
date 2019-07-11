---
layout: post
title:  "[Data Structure 1] LinkedList (연결리스트)"
date:   2019-07-09
excerpt: "linkedlist basics, comparison with array, implementation, and time complexity"
tag:
- linkedlist
- data structure
- javascript
comments: true
feature: https://images.unsplash.com/photo-1552550049-db097c9480d1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1234&q=80
---

# LinkedList (연결리스트)

+ [Basics](#basics)
+ [Comparison with Array](#linkedlistvsarray)
+ [Real Life Use Case](#reallifeusecase)
+ [Implementation](#implementation)
+ [Time Complexity](#timecomplexity)


<h2 id='basics'>LinkedList Basics</h2>
![alt](https://s3-us-west-2.amazonaws.com/ib-assessment-tests/problem_images/singly-ll.png)

LinkedList는 노드(node)들로 이루어진 선형 자료구조이며, 각각의 노드는 두개의 값을 가지고 있다.

하나는 노드에 입력한 자료의 값이고, 다른 하나는 다음 노드에 대한 레퍼런스 값이다.

위의 이미지에서 head 와 tail 부분을 잠시 제쳐두고 보면, 노드의 한칸엔 숫자값이 있고, 다른칸에는 그 다음 노드를 가리키는 화살표, 즉 레퍼런스값을 가지고 있는 것을 볼 수 있다.

가장 첫 노드는 머리(head)라고 하고 linkedlist의 head property로 레퍼런스할 수 있으며,  
가장 마지막 노드는 꼬리(tail)라고 하고 마찬가지로 tail property로 레퍼런스할 수 있다.

위의 그림에서 tail이 레퍼런스하는 노드, 즉 마지막 노드에는 화살표가 없이 줄이 그어져있는 것을 볼 수 있는데, 그 이유는 마지막 노드는 그 다음 노드가 존재하지 않고, 레퍼런스값을 가지지 않고 있기 때문에 레퍼런스 값이 null인 것과 마찬가지다.

만약 Linkedlist에 노드가 하나만 존재한다면, 그것은 머리 속성으로 레퍼런스 할수있고, 꼬리 속성으로도 레퍼런스 할수있다. 

#### Summary

+ LinkedList는 노드라는 단위로 이루어져 있다.
+ 각각의 노드에는 두가지의 값이 존재하는데, 하나는 노드가 가진 고유의 자료값이고 다른하나는 다음 노드를 가리키는 레퍼런스값이다.
+ 가장 첫 노드는 머리(head)라고 하고 맨 마지막 노드는 꼬리(tail)라고 한다.
+ 꼬리 노드에는 레퍼런스하는 값이 (null)이다.

<h2 id='linkedlistvsarray'>LinkedList vs. Array</h2>

#### Advantages

LinkedList가 Array와 비교했을 때 가진 장점 두가지를 꼽자면 하나는 dynamic size 이고 다른 하나는 ease of insertion and deletion 이다.

+ Dynamic Size: LinkedList는 노드를 추가/제거함에 따라 사이즈가 늘어나고 줄어들면서 사이즈가 바뀌지만, 배열은 생성시에 정한 사이즈이고 사이즈를 늘리거나 줄이려면 배열을 조작해야한다. 
+ Ease of insertion and deletion: 배열은 엘레먼트를 추가하거나 제거하려면, 자리를 만들고 기존에 존재하는 엘레먼트들을 한칸씩 움직여줘야하는데, LinkedList는 원하는 위치에 존재하는 노드와 추가되는 노드의 레퍼런스 값만 조정하면 된다.

#### Disadvantages

+ Random access is not allowed: LinkedList는 원하는 노드에 접근을 할 때 무조건 맨 처음 노드, head로 부터 시작해야한다는 단점이 있다.  
+ Extra memory space for a pointer is required with each element of the list: 한 단위당 하나의 고유 값만 가지고 있는게 아니라 다음 노드에 대한 레퍼런스값(pointer)도 가지고 있기 때문에 다른 자료구조에 비해 메모리공간을 추가적으로 차지한다.

<h2 id='reallifeusecase'>Real Life Use Case</h2>

- Image Viewer
  - 이미지 뷰어에서 전 이미지와 그 다음 이미지는 서로 연결 되어있다. 그러므로 이전과 다음 버튼을 이용해 이미지를 순차적으로 볼 수 있다.
- Music Player
  - 뮤직 플레이어에서도 위와 마찬가지로 이전 노래는 다음 노래에 대한 포인터가 있고 다음 노래는 이전 노래에 대한 포인터가 있다. 이전과 다음 버튼을 이용하여 이전 노래와 다음 노래를 오갈 수 있다. 
- Previous and Next Page on Web Browser 
  - 웹브라우저의 페이지들도 위와 같은 맥락으로 이전 페이지와 다음 페이지가 연결되어있다.

<h2 id='implementation'>LinkedList Implementation</h2>

먼저 linkedlist 라는 객체를 만들 생성자 함수를 만든다.

~~~javascript
function LinedList () {
  var list = {};
  list.head = null;
  list.tail = null;
  
  return list;
}
~~~

function 은 list라는 빈 객체를 리턴하고, 이 list 객체에는 head와 tail이라는 property를 준다.  

현재는 list 객체 안에 아무런 노드도 없기 때문에 head와 tail의 레퍼런스 값은 null 이다.  
  
--- 
LinkedList에 addToTail, removeHead, contains method들을 추가한다.
~~~javascript
function LinkedList () {
  var list = {};
  list.head = null;
  list.tail = null;
  
  list.addToTail = function(value) {};

  list.removeHead = function() {};

  list.contains = function(target) {}

  return list;
}
~~~
---
LinkedList는 노드라는 객체가 단위를 이루고 있기 때문에, Node라는 생성자 함수를 추가한다. 
~~~javascript
function Node (value) {
  var node = {};
  node.value = value;
  node.next = null;

  return node;
}
~~~
Node 생성자함수는 node에 들어갈 값을 인자로 받고, 그 인자를 새롭게 생성되는 노드의 value property에 넣는다.
아직 다음 노드가 없으므로 next property는 null 이다.  
이제 노드를 만들 수 있으니, LinkedList에 addToTail method를 구현하여 연결리스트에 노드를 추가해보자.

---
~~~javascript
  list.addToTail = function (value) {
    var newNode = Node(value);
    if (!list.head) {
      list.head = newNode;
    }
    if (!list.tail) {
      list.tail = newNode;
    } else {
      list.tail.next = newNode;
      list.tail = newNode;
    }
  };

~~~
Node생성자 함수에 addToTail로부터 받아온 value값을 넣어 새 노드를 생성한다.  
그리고 만약 연결리스트에 머리와 꼬리가 null 일 경우 머리와 꼬리 레퍼런스를 새 노드로 가리킨다.  
꼬리가 가리키는 값이 존재할 경우에는 그 값의 다음(next)를 새 노드로 지정하고, 꼬리는 새 노드로 만든다. 

---

removeHead는 머리를 제거하고, 그 머리에 든 값을 리턴하는 method이다.  
removeHead도 위와 마찬가지로 비슷한 방식을 이용해 구현하면 된다. 
~~~javascript
list.removeHead = function () {
  var removedHeadVal = list.head.value;
  list.head = list.head.next;
  return removedHeadVal;
}
~~~

---

마지막으로 contains 를 구현해보자

~~~javascript
list.contains = function (target) {
  var currentNode = list.head;
  while (currentNode) {
    if (currentNode.value === target) {
      return true;
    } else {
      currentNode = currentNode.next;
    }
  };
  return false;
}
~~~

LinkedList는 search를 할때 항상 머리부터 시작해야하므로, currentNode라는 변수를 list.head로 놓는다.  
그리고 currentNode라는 변수가 존재하는 동안, 즉 null이 아닌 동안 while loop을 실행한다.  
while loop 안에는 currentNode의 value값과 target값을 비교하는 if문이 있고, 만약 같다면 true를 리턴한다  
같지 않을 경우 currentNode 변수를 currentNode.next로 할당하고 while loop이 다시 시작된다.  

while loop이 끝나고도 target값과 일치하는 노드의 값을 찾지 못했다면 해당 연결리스트에는 찾고자하는 값이 존재하지 않으므로 false를 리턴한다.

---

이와같이 간단한 LinkedList 자료구조를 구현해볼 수 있다!

~~~javascript
var LinkedList = function() {
  var list = {};
  list.head = null;
  list.tail = null;

  list.addToTail = function(value) {
    var newNode = Node(value);
    if (!list.head) {
      list.head = newNode;
    }
    if (!list.tail) {
      list.tail = newNode;
    } else {
      list.tail.next = newNode;
      list.tail = newNode;
    }
  };

  list.removeHead = function() {
    var removedHeadVal = list.head.value;
    list.head = list.head.next;
    return removedHeadVal;
  };

  list.contains = function(target) {
    var currentNode = list.head;
    while (currentNode) {
      if (currentNode.value === target) {
        return true;
      } else {
        currentNode = currentNode.next;
      }
    }
    return false;
  };
  return list;
};

var Node = function(value) {
  var node = {};
  node.value = value;
  node.next = null;
  return node;
};

~~~

<h2 id='timecomplexity'>Time Complexity (시간복잡도)</h2>

#### 1. addToTail

~~~javascript
  list.addToTail = function (value) {
    var newNode = Node(value);
    if (!list.head) {
      list.head = newNode;
    }
    if (!list.tail) {
      list.tail = newNode;
    } else {
      list.tail.next = newNode;
      list.tail = newNode;
    }
  };
~~~

addToTail은 linkedlist의 tail property를 통해 바로 tail로 새로운 노드를 추가할 수 있다.  
이 method는 linkedlist의 **사이즈에 무관하게 항상 동일한 양의 작업 혹은 시간이 소요된다.**   
그리고 head부터 tail까지 하나하나 찾아봐야하는 연산작업을 필요로 하지 않는다.  
>그러므로 이 method의 time complexity는 **O(1)** 이라고 볼 수 있겠다.

#### 2. removeHead

~~~javascript
list.removeHead = function () {
  var removedHeadVal = list.head.value;
  list.head = list.head.next;
  return removedHeadVal;
}
~~~
removeHead는 addToTail과 비슷한 맥락으로 head property를 이용한 head에 손쉬운 접근이 가능하다.  
>이 역시 연결리스트의 크기에 의존하지 않는 작업이므로 time complexity는 **O(1)** 이다.

#### 3. contains

~~~javascript
list.contains = function (target) {
  var currentNode = list.head;
  while (currentNode) {
    if (currentNode.value === target) {
      return true;
    } else {
      currentNode = currentNode.next;
    }
  };
  return false;
}
~~~

contains는 연결리스트 안에 target 값이 존재하는지 판단하여 boolean value를 리턴하는 메소드이다.  
이 target값은 연결리스트의 마지막인 꼬리에 있을 수도 있고, 중간 노드에 있을 수도 있고, 가장 처음인 머리에 있을 수도 있는 가능성이 있기 때문에, 연결리스트의 크기와 상관이 있는 작업이다.  
target값이 꼬리에 있다면 머리부터 시작해서 순차적으로 노드를 거쳐가며 꼬리에 도달하기까지의 작업 혹은 시간이 소요된다.  
>이 시간은 연결리스트의 사이즈인 n에 의존하는 작업이므로 time complexity는 **O(n)** 이라고 할 수 있다. 

## Other Types of LinkedLists

- singly linkedlist
- doubly linkedlist
- etc.
