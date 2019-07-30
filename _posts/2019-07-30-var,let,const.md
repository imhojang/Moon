---
layout: post
title:  "var, let, and const - what's the difference?"
date:   2019-07-30
excerpt: "ES2015 (ES6) 가 2017년도에 출시되면서 많은 기능들이 추가되었다. 오늘은 var과 let 그리고 const의 각각의 특징과 사용용도에 대해 알아보았다."
tag:
- javascript
- variables
- var
- let
- const
- grammar
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
---

### VAR

- Scope

  - **스코프:** 함수를 기준으로 스코프가 생긴다

    - 변수가 사용가능한 영역을 가리킨다.
    - var 선언은 글로벌 혹은 로컬 스코프이다.
    - 함수밖에서 선언되면 글로벌 스코프가 된다.
    - 함수안에서 선언되면 로컬 스코프가 된다.
    - 로컬 스코프가 되면 해당 함수 안에서만 사용이 가능하고 밖에서는 사용이 불가능해진다.

  - **재선언**과 **업데이트**가 가능하다.

    ```js
    var greeter = 'hey hi';
    var greeter = 'say Hello instead;'
    greeter = 'bonjour';
    ```

  - **호이스팅 (Hoisting)**

    - 호이스팅은 자바스크립트에 있는 메커니즘으로, 변수와 함수 선언이 현재 속한 스코프의 최상단에 위치하게 되는 것을 말한다. 

    - ```js
      console.log(greeter);
      var greeter = 'say hello';
      ```

    위는 다음과 같이 해석된다.

    ```js
    var greeter;
    console.log(greeter);  // greeter is undefined
    greeter = "say hello"
    ```

    > var 로 선언된 변수들은 최상단으로 끌어올려지면서 undefined의 값으로 초기화 된다.


### LET

- Scope

  - **스코프:** 블록 스코프

    - let으로 선언된 중괄호 { }안을 기준으로 스코프가 생긴다.

      ```js
      let greeting = "say Hi";
      let times = 4;
      if (times > 3) {
        let hello = "say Hello instead";
        console.log(hello); // say hello instead;
      }
      console.log(hello); // hello is. ot defined
      ```

    - **변경은 가능**하지만 **재선언은 불가능**하다

      ```js
      let greeting = "say Hi";
      greeting = "say Hello instead";
      ```

      ```js
      let greeting = "say Hi";
      let greeting = "say Hello instead"; //error: Identifier 'greeting' has already been declared
      ```

    - **다른 스코프에선 재선언이 가능**하다. 아래와 같은 경우에선 에러가 나지 않는다.

      ```js
      let greeting = "say Hi";
      if (true) {
        let greeting = "say Hello instead";
        console.log(greeting); // "say Hello instead"
      }
      console.log(greeting); // "say Hi"
      ```

      에러가 생기지 않는 이유: 두 인스턴스는 다른 스코프에 속해 있기 때문에 서로 다른 변수로 간주된다.

- Hoisting of `let` 

  - 호이스팅
    - `var` 선언과 같이 `let` 선언도 호이스팅 된다. 호이스팅시에 `var` 의 값은 정의 되기전까진 undefined로 초기화 되지만, `let` 의 값은 초기화 되지 않는다. 그렇기 때문에 `let` 변수가 선언이 되기 전에 그 변수를 사용하려한다면 `Reference Error` 이 생긴다.

### CONST

- `const` 키워드로 선언된 변수는 `let` 과 비슷한 점들이 있다.

  - **블록스코프**
  - 한번 `const` 키워드로 선언된 변수는 **변경과 재선언이 모두 불가**능하다.

  ```js
  const greeting = "say Hi";
  greeting = "say Hello instead"; //error : Assignment to constant variable
  ```

  ```js
  const greeting = "say Hi";
  const greeting = "say Hello instead"; //error : Identifier 'greeting' has already been declared
  ```

  - **하지만 `const` 로 선언된 Object의 속성은 변경이 가능하다.** 

    ```js
    const greeting = {
      message : "say Hi",
      times : 4
    }
    
    const greeting = {
      words : "Hello",
      number : "five"
    } //error : Assignment to constant variable
    ```

    위는 변경이 불가능하지만 아래는 에러가 없이 변경이 가능하다

    ```js
    greeting.message = "say Hello instead";
    ```

  - Hoisting of `const` 
    - ​	let과 같은 규칙을 따른다.

### **요약**

#### **var**

- **함수를 기준으로 스코프가 생거기거나 전역변수가 된다.**
- **변경과 재선언이 가능하다.**
- **호이스팅되면서 값이 undefined로 초기값이 설정된다.**
- **초기값을 명시하지 않아도 선언이 가능하다**

#### **let**

- **블록 스코프 : 중괄호를 기준으로 스코프가 생긴다.**
- **변경은 가능하고 재선언은 불가능하다.**
- **호이스팅되면서 초기값이 설정 되지 않는다. -> 선언 전 까진 사용 불가능**
- **초기값을 명시하지 않아도 선언이 가능하다**

#### **const**

- **블록 스코프 : 중괄호를 기준으로 스코프가 생긴다.**
- **변경과 재선언이 모두 불가능하다. 하지만 object는 속성 접근으로 변경이 가능하다.**
- **호이스팅되면서 초기 값이 설정 되지 않는다. -> 선언 전 까진 사용 불가능.**
- **선언시 초기값을 명시해야한다.** 초기값을 명시하지 않아도 선언이 가능하다

