---
layout: post
title: "[Web Foundation] Session vs Token based Authentication"
date: 2020-01-14
excerpt: " "
tag:
    - HTTP
    - Cookie
    - Session
    - Token
    - Authentication
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [Javascript]
---

>쿠키에 대해 알아보았으니 이번 포스트에서는 세션과 토큰 인증 방법에 대한 내용을 다뤄보려고 한다. 세션과 토큰 모두 웹상에서의 인증 과정을 논할 때 자주 보이는 키워드들인데, 막상 생각해보면 이 마저도 정리가 잘 되어있지 않아있다. 웹상에서 사용자 인증을 거칠 때 주로 사용되는 세션과 토큰 인증 방식. 각각의 특징과 장단점들을 알아보자.

지난 쿠키에 관한 포스트에서도 언급했지만, HTTP (hypertext transfer protocol)는 비연결지향적(Connectionless)이고 상태를 유지하지 않는 특성(Stateless)이 있다. 하지만 상태를 유지해야만 하는 상황이 있다. 온라인 쇼핑몰에서 장바구니에 물건을 담을 때를 예로 들어보자. 감자를 장바구니에 담고, 소고기를 담기 위해 다른 페이지로 이동할 때 감자는 장바구니에서 사라지지 않고 계속해서 담겨있어야 한다. 즉, 온라인 쇼핑몰에서 장바구니에 담겨있는 물건들에 대한 정보, 장바구니 상태를 지속적으로 유지하고 있어야 한다는 것이다.

상태를 유지하지 않는 HTTP의 특성을 극복하기 위해 우리는 세션 혹은 토큰을 사용하는 방법이 있다.

우선 세션기반 인증방법에 대해 알아보자.

### 세션이란?

세션은 일정 시간동안 같은 사용자(정확히는 브라우저)로 부터 들어오는 일련의 요구를 하나의 상태로 보고 그 상태를 일정하게 유지시키는 기술 이라고 한다.

### 여기서 말하는 일정 시간이란?

방문자가 웹 브라우저를 통해 웹 서버에 접속한 시점으로부터 웹 브라우저를 종료함으로써 연결을 끝내는 시점.  

즉, 방문자가 웹서버에 접속해 있는 상태를 하나의 단위로 보고 세션이라 칭한다.



### 

<img src='https://i1.wp.com/4.bp.blogspot.com/-FnbFMxnKkV4/WV565AN7ifI/AAAAAAAAQZg/5_p-m1oxBqUx2CCqyqS3Y9JAUwmGO34nQCLcBGAs/s1600/1.png?w=687&ssl=1' alt='session-authentication-flow'/>



### P.S. (postscript/afterthought)
