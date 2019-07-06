---
layout: post
title:  "[Problem Solving] pageCount"
date:   2019-05-08
excerpt: "my take on pageCount using JS"
tag:
- markdown 
- syntax
- sample
- test
- jekyll
comments: true
feature: https://images.unsplash.com/photo-1453733190371-0a9bedd82893?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1267&q=80

---

### 교과서 넘기기 (pageCount)
---
###### 문제 이해 :
  * **Arguments**  
  (1) n : total number of pages in the book  
  (2) p : page of interest
  * **Conditions**  
  (1) end goal is to *reach the page of interest*  
  (2) must begin flipping pages on either *the first page or the last page* of the book  
  (3) must flip *one page at a time* to reach the page of interest  
  (4) the book is read from left to right direction
  (5) page 1 will always begin on the *right side*  
  (6) last page can either be on left or right side *depending* on the total number of pages in the book
  * **Return**  
  (1) return the *minimum* number of page flips required to reach the page of interest

###### 해결 방법 :  
  * **Decide where to begin (front or back)** If the page of interest is greater than half of total number of pages, start from the last page. Else, start from the first page. Then,
  * **Create a for loop** that increments/decrements page number by 2 everytime the loop is run. This loop should stop and return the number of flips if current page is equal or greater/less than the page of interest.  
  If the book is read from the front, current page should equal or be greater than the page of interest. However, if flipping starts from the back, current page should equal or be less than the page of interest.
###### 코드 구현 :  
  ```javascript
  function pageCount(pagesTotal, page) {
    if (page <= pagesTotal / 2) {
      var currentPage = 1;

      for (var flips = 0; currentPage < pagesTotal; flips++) {
      if (currentPage >= page) return flips;
      currentPage += 2;
      }
    } else {
      var currentPage = pagesTotal;

      for (var flips = 0; currentPage > pagesTotal / 2; flips++) {
      if (currentPage <= page) return flips;
      currentPage -= 2;
      }
    }
  }
  ``` 

###### 결과 분석 : 

  * **test case 1 failed** "expected 1 to deeply equal 0"  
    * There was an extra flip in the loop when started from the back of the book when the page
  * **test case 2 failed** "expected 71 to deeply equal 70"  
    * same problem occurred as above

###### 해결 방법 : 

  * **Account for odd number of total pages** so that there is no extra flip to reach the page of interest.  
    * If the total number of pages is an odd number, subtract one from it and set it as the current page.
    * If the total number of pages is an even number, set it as the current page.

###### 코드 구현 : 
```javascript
  function pageCount(pagesTotal, page) {
    if (page <= pagesTotal / 2) {
      var currentPage = 1;

      for (var flips = 0; currentPage < pagesTotal; flips++) {
      if (currentPage >= page) return flips;
      currentPage += 2;
      }
    } else {
      var currentPage = pagesTotal % 2 === 0 ? pagesTotal : pagesTotal - 1;

      for (var flips = 0; currentPage > pagesTotal / 2; flips++) {
      if (currentPage <= page) return flips;
      currentPage -= 2;
      }
    }
  }
```
###### 결과 분석 : 

  * **All tests passed !** 

  ![pikachu](/assets/postimg/pikachu.jpg "$50 dollar pikachu that I won")