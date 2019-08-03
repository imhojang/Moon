---
layout: post
title:  "Introduction to Hash Table, Tree, and Complexity Analysis"
date:   2019-07-10
excerpt: " "
tag:
- hash table
- tree
- Big O
comments: true
feature: https://images.unsplash.com/photo-1552550049-db097c9480d1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1234&q=80
category: [ Data Structure ]
---

# Hash Table

**가장 중요한 것 중 하나!**

Process your key through a hashing function which converts to an addressable space.

Since we cannot manage low level memory with Javascript, we will just use an empty array.

Big O (when there are no collisions)

- Insertion: O(1)

```javascript
function hash(key) {
  for (var i = 0; i < key.length; i++) {
    for (var j = 0; j < key.length; j++) {
      // hash
    }
  }
}
```

만약 hash 함수가 O(n^2)이더라도 hash table에 추가하는 것을 기준으로 보았을 때 항상 동일한 시간/작업이 걸리기 때문에 Insertion은 O(1)이다.

- Deletion: O(1)
- Search: O(1)

------

Is Hash Table perfect?

- not suitable for **ordered data**
- might need large space allocation 공간적인 사전 조건이 필요함.
- must have a good hash function

------

What is hashing?

Taking an **input string** of any length and giving out an **output of a fixed length**

ex) MD5.. SHA.. and etc => well known hashing function (low probability of collision)

------

Hash function

Hash function needs to be **idempotent.**

```javascript
function hash(k) {
  return 2 * k;
  // hash (2) will always output 4.
}
```

: A function given an input always outputs the same output.

Hash function needs to have a **good distribution of values.**

Hash function needs to be **performant.**

------

Real Life Use Cases

- Address Book
- Blockchain
- javascript, chrome web browser engine, etc.

------

Hash Tables in Javascript

A lot of times, we use Javascript Plain Objects in the place of Hash Table.

Javascript is High Level Language.

Programmers dont manage memory themselves.

Javascript Objects use Hash Tables.

Javascript Map is not stable yet.

------

# Tree

What is **"node"**?

A [node](<https://en.wikipedia.org/wiki/Node_(computer_science)>) is **a basic unit** used in computer science.

------

Real Life Use Cases

- DOM
- File System

------

Binary Search Tree (이진 탐색 트리)

- Tree structure in which a node can have zero, one, or two subtrees.
- Every node in the **left** has a **smaller value** than its parent node.
- Every node in the **right** has a **bigger value** than its parent node.

------

Big O - average

- Insertion: O(log n)
  - 반이 항상 나눠지기 때문에, 반씩 확인해 나가는 것이기 때문에 반씩 줄어 들고 그건 log n 을 따른다.
  - [참고문서](https://hackernoon.com/what-does-the-time-complexity-o-log-n-actually-mean-45f94bb5bfbf)
- Deletion: O(log n)
- Search: O(log n)

Big O - worst Cases

- Insertion: O(n)
- Deletion: O(n)
- Search: O(n)

------

Real Life Use Cases

- Searching in an ordered data
  - 1 부터 20 까지 있는 순서가 있는 자료구조에서 4 를 찾고 싶으면 반을 잘라 내면서 4를 찾아가는 것
- AVL Tree, Red Black (Trie) are more useful in real scenarios, because they are self balancing
  - 치우치지 않도록 자료를 재분포하기 때문에 항상 log n 의 time complexity를 따른다

------

Binary Tree vs. Binary Search Tree

- Binary Tree: 자식노드가 최대 2개