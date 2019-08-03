---
layout: post
title:  "Server & Client & HTTPS"
date:   2019-06-17
excerpt: " "
tag:
- javascript
- server 
- client 
- https
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ Javascript ]
---

### Date: 2019-06-17 19:37:13

 Today's Lesson:

# Server & Client & HTTPS

**개발자에게 서버란?**

- A computer which manages acess to a centralized resource or service in a network.
- 네트워크상에서 어떠한 자료 또는 서비스에 대한 접근을 관리하는 컴퓨터
- 웹에서 말하는 서버란 자고로 네트워크에 연결되어 있어야 한다.

**네트워크에 연결된다면?**

- 네트워크에 연결되면, IP 주소를 부여받게 된다. IP 주소를 부여받는다면 다른컴퓨터들이 해당주소로 방문할 수 있다.
- 그리고 클라이언트들이 해당 주소로 주문을 받을 수 있다.
- 웹 네트워크상의 컴퓨터마다 할당되는 주소

**IP 주소란 무엇인가?**

- 네트워크 환경에서 컴퓨터(노드)간 통신하기 위해 각 컴퓨터에 부여된 네트워크 상 주소

**도메인이란 무엇인가?**

- ip는 사람이 이해하고 기억하기 어렵기 때문에 이를 위해서 각 ip에 이름을 부여할 수 있게 했는데, 이것을 도메인이라고 한다.

naver.com -> 220.95.233.172  
daum.net -> 114.108.157.19

**개발자에게 클라이언트란?**

- 서버에 있는 자료를 접근할 수 있는 프로그램
  1. 웹 브라우저 
  2. 핸드폰 어플리케이션
  3. 데스크탑 어플리케이션

### 구글닷컴에 방문하는 시나리오 

1. 클라이언트: 사용하는 브라우저
2. 서버: 구글 홈페이지 HTML을 관리하는 네트워크상의 컴퓨터

### 브라우저가 구글 서버로 HTML 한개 주문을 넣어야 한다. 구글 서버의 주소를 어떻게 알아낼까? 

### -> DNS Server

**D**omain  
**N**ame  
**S**ystem 

모든 웹 서버들의 주소를 우리가 외우고 있을수는 없기 때문에, 
DNS 서버들이 클라이언트들이 IP 주소를 쉽게 찾을 수 있도록 인터넷 주소록 역할을 해준다.


# 클라이언트와 서버가 정보를 어떻게 주고 받을까?

### HTTP (HyperText Transfer Protocol)

**웹**에서 주고 받는 메시지에 대한 규칙의 정의 (규약)

브라우저에서의 통신이 아니더라도, 웹 상에서의 모든 주고받는 메시지에 대한 것.

웹에서 메시지 교류는 어떠한 형식으로 이루어져야 하는지, 요청과 응답

- 웹이라는 나라에는 여러 가지의 길이 있다. 인도, 차도, 자전거 전용도로 등..
- HTTP란 이런 길 위를 지나다닐떄 지켜야하는 규칙들의 정의를 뜻한다.

꼭 반드시 지켜야하는 것은 아니다. 하지만 오랜 시간동안 사용되며 검증된 시스템이다.

## Request - 요청 (주문)

클라이언트 1: 여기 index.html 한개요.
클라이언트 2: 여기 index.css 한개요.

## Response - 응답 (답변)

서버 1: 주문하신 index.html 나왔어요
서버 2: 주문하신 index.css. 나왔어요

------

## what if a server accepts HTTP requests from any Client

For example, anyone can make HTTP requests to a bank server
of course the bank server has some security logic. but does that make this server really safe?

## CORS (Cross Origin Resource Sharing) Policy

- 브라우저에만 있는 추가적인 보안. 한 도메인에서 다른 도메인으로 접근하는 것을 막음. 어떤 웹사이트에 접속을 했는데 자바스크립트가 로드되면서 그걸로 신한은행 쿠키를 이용하여 접속을 할 수 있으므로, 이런 악용을 막기위한 정책. CORS 는 웹 브라우저에 탑재된. 브라우저에 한하는 기능이자 규칙이자 정책이다.

All browsers simply restrict script-based network calls to their own domain to make it simple and safe.

Site X at www.x.com cannot make AJAX requests to site Y at www.y.com. 

If you want to accept AJAX requests from other site/domains, it must be configured **on the server** list.

There are some exceptions to CORS policy :

- \<video>

- \<img>

- \<script>
 

  You can load any resources from any domain using above HTML tags

(CORS는 흔한 인터뷰 질문임)
 
More...

#### JSONP (CORS와 같이 봐야함)

#### Preflight Requests


# AJAX asynchronous javascript and XML

전체 페이지를 새로고칠 필요없이 서버와 정보를 교환하고 웹페이지의 일부만을 수정할 수 있게하는 방법.

### Classic Web Application Model

Ajax가 통용되기 이전에는 웹페이즈에 보여줄 새로운 정보가 있다면 

1. HTML
2. DOM
3. javascript
4. XMLHttpRequest

# HTTP Request

HTTPS 를 쓴다고 http request 포맷이 바뀌지는 않음.

**https** 를 쓰면 암호화된 관을 통해가는 거와 같음.
http를 쓰면 비닐로 이루어진 관을 통해가는 거와 같음.

# Request Methods HTTP 규약에 정의된 메소드들

- GET - 찾기 (무언가를 달라)  
  - body가 가야하는 경우는 거의 없음
- POST - 생성하기 (서버쪽에 뭔가를 만들고 싶다는 것임 ) ex 회원가입시 사용자정보를 입력할때 
  - body가 가야하는 경우는 보통 있음
    만들어달라고 요청.  
- PUT - 수정하기. 수정할려고 주문을 넣는것임. 
  - body가 가야하는 경우가 보통 있음
- DELETE - 지우기 

이 메소드들을 사용하기 헷갈릴떄가 많기 때문애 인터넷검색을 활용해야함

# HTTP responses

request 와 거의 비슷한 포맷임.

403 - 응답코드 response code = Forbidden을 뜻 함. 
=> 금지된 주문을 요청한거라는 뜻

# Response code

- 1XX
  - (생략)
- 2XX
  - (Success)
  - POST method 로 요청을 하고 201로 응답코드가 오면 잘 생성되었다는 뜻임.
  - GET method 로 요청을 하고 200로 응답코드가 오면 잘 찾아왔다는 뜻임. body 에 가져온 정보 포함
- 3XX
  - (Redirection) 우회
  - 다른 서버로 요청을 우회시킴.
- 4XX
  - Client Error
  - 주문이 이상해
- 5XX
  - Server Error

# JSON (javascript object notation)

- Made by [Douglas Crockford](https://en.wikipedia.org/wiki/Douglas_Crockford) 
- JSON 은 key 값을 쓸때 꼭 쌍따옴표를 써야함 ""
- JSON 이란 객체의 stringfy 메소드를 쓰면 자바스크립트를 json포맷으로 바꿀 수 있고
- parse란 메소드를 쓰면 json 을 javascript 포맷으로 바꿔준다.