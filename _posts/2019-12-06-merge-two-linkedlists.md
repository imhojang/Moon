---
layout: post
title:  "[Problem Solving] mergeTwoListedLists (LeetCode-Easy)"
date:   2019-12-06
excerpt: ""
tag:
- javascript
- algorithm
- linkedlist
- LeetCode
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ Algorithms ]
---

### Merge Two Sorted Lists (정렬된 두 연결리스트 합병하기)


##### Problem Description:

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

> 정렬된 두 연결리스트를 합병하여 새로운 연결리스트를 반환하세요. 새로운 연결리스트는 기존의 두 연결리스트의 노드들을 자르고 이어붙이면서 만들어야합니다.

Example:

```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

##### Sudo Code:

1. val과 next가 있는 dummy 노드를 만들어서 Head로 지정한다.
2. runner 변수는 처음엔 Head를 가리키도록 한다.
3. 두 리스트의 노트가 각각 존재하는한 둘이 비교하도록 한다.
4. 예를 들어, l1의 val 값이 l2의 val 값 보다 크다면, runner의 다음은 l2를 가리키게 한다. 
5. l2 노드는 새로운 연결리스트에 포함됬으므로 l2에 l2의 다음 노드를 가리키게한다
6. 반대로 l1의 값이 l2의 값보다 작다면 runner의 다음을 l1에 가리키게한다.
7. 만약 기존의 두 연결리스트의 노드 중 하나가 더 이상 없다면 l1 혹은 l2를 가리키게 한다. (l1과 l2는 이미 정렬 되어있는 연결 리스트므로서 가리키게 해도 정렬된 순서에서 벗어나지 않는다)

##### Code:

```js
function mergeTwoLinkedLists (l1, l2) {
  var headDummyNode = { val: null, next: null };
  var runner = headDummyNode;

  while (l1 && l2) {
    if (l1.val > l2.val) {
      // l2가 더 작으므로 runner.next에 작은 l2를 가리키게한다.
      runner.next = l2;
      l2 = l2.next
    } else {
      // l1이 더 작으므로 runner.next에 작은 l1을 가리키게한다.
      runner.next = l1;
      l1 = l2.next
    }
    // runner이 가리키는 대상을 방금 이어붙인 노드로 옮긴다.
    runner = runner.next
  }
  // l1이나 ㅣ2 둘 중 하나라도 노드가 존재하지 않을 경우 while loop이 break한다.
  // 그러면 단순하게 runner.next는 둘 중 존재하는 노드를 가리키게 하면 정렬이 끝난다.
  // ex) input이 1->2->3, 10->20->30 라면 위의 while loop에서 l1은 null이 되고
  //  l2는 10에 머물게 된다. 그리고 l2는 정렬되어있으므로 10 값이 들어있는 노드를 runner이
  //  가리키게 되면 정렬은 끝난다. 1->2->3->10->20->30
  runner.next = l1 || l2

  // headDummyNode는 임의로 만들어준 값이고 그 다음부터가 진짜 정렬된 리스트므로
  // headDummyNode.next를 반환한다.
	return headDummyNode.next
}
```



