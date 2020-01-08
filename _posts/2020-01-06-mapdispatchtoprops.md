---
layout: post
title:  "[React-Redux] mapDispatchToProps의 다양한 사용법"
date:   2020-01-06
excerpt: " "
tag:
- React
- Redux
- mapDispatchToProps
- ES6
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ Javascript ]
---

**이 글은 리액트를 이용하여 프로젝트를 진행한 경험이 있고, 리덕스에 대한 기초적인 이해가 있는 사용자들을 대상으로 작성한 것입니다.**

>mapDispatchToProps의 형태는 두가지가 있다. 하나는 함수형태이고 다른 하나는 객체형태다.

오늘 중점적으로 다룰 내용은 mapDispatchToProps의 형태이다. 그전에 앞서 mapDispatchToProps가 어떤 역할을 하는지 간략히 알아보자.

### mapDispatchToProps란?

리액트를 사용할 때 예측가능한 상태관리를 위해 리덕스 라이브러리를 사용하게 된다. 리덕스 사용법을 배우다 보면 필연적으로 마주치는 mapDispatchToProps와 mapStateToProps가 있다. 오늘은 mapDispatchToProps의 다양한 사용례에 대해 알아볼 것이다.


몇몇의 예외를 제외하고는 대개 이름을 자세히 살펴보면 그 대상이 무슨 역할을 하는지 유추할 수 있다. 이름은 어떤 한 대상이 무엇인지, 무슨 역할을 하는지 쉽게 알 수 있도록 고민에 고민을 걸쳐 하여 나온 산물이기 때문이다.

mapDispatchToProps를 직역하자면, map (맵핑한다) Dispatch (디스패치를) ToProps (프롭에). 즉, 디스패치를 프롭에 맵핑한다는 것을 뜻한다.

이쯤에서 전반적인 mapDispatchToProps의 사용례를 한번 보자.

```js
const someActionCreator = (a) => {
  return {
    type: 'SOME_ACTION',
    payload: a
  }
}

const mapDispatchToProps = (dispatch) => {
  return {
    someActionCreator: (a) => dispatch(someActionCreator(a))
  }
}
```

mapDispatchToProps 함수는 dispatch를 인자로 받고 어떤 객체를 반환한다. 이 객체에는 someActionCreator이라는 액션생성함수의 실행의 결과값인 액션객체를 dispatch로 감싸서 반환하는 함수가 키값과 맵핑되어 들어있다.

mapDispatchToProps는 주로 이러한 형태를 띄게된다. 이렇게 하면 연결된 컴포넌트에선 someActionCreator을 prop으로 받아 볼 수 있게된다. 여기까지는 리덕스를 사용해 본 경험이 있다면 모두 흔히 알고 있는 부분이다.

#### ownProps

> mapDispatchToProps가 함수형태일 경우에는 첫번째 인자로 dispatch를 받고, 두번째 인자로 ownProps를 받는다.

[리액트-리덕스 공식문서](https://react-redux.js.org/using-react-redux/connect-mapdispatch#arguments)에 이에 대한 내용이 나와있다.

ownProps는 dispatch와는 다르게 optional 이다. 그리고 필요한 상황에서만 쓰이기 때문에 많은 리덕스 설명에서 생략하곤 하는 것 같다.

```js
// (A) binds on component re-rendering
<button onClick={() => this.props.toggleTodo(this.props.todoId)} />

// (B) binds on `props` change
const mapDispatchToProps = (dispatch, ownProps) => {
  toggleTodo: () => dispatch(toggleTodo(ownProps.todoId))
}
```

ownProps는 순수 자바스크립트 오브젝트의 형태로 부모에게 받은 props가 들어있다. 연결된 컴포넌트가 부모 컴포넌트로부터 전달받은 props를 mapDispatchToProps내에서 사용할 수 있게 하는 역할을 한다.

ownProps를 사용하게 되면 props가 바뀔 때마다 새로 바뀐 props가 액션크리에이터에 재바인딩 된다. 

흥미로운 사실 한가지는 react-redux의 저자 Dan Abramov는 props가 바뀔 때마다 액션 디스패쳐에 prop을 재바인딩(B) 하므로 컴포넌트가 리랜더링 될 때 액션 디스패쳐에 재바인딩 하는 편(A)이 속도 측면에서 더 빠를 것이라 했다.

[Dan Abramov의 글은 여기에서 볼 수 있다.](https://github.com/reduxjs/redux-devtools/issues/250#issuecomment-186429931)

#### bindActionCreators

```js
const mapDispatchToProps = dispatch => {
  return {
    increment: () => dispatch(increment()),
    decrement: () => dispatch(decrement()),
    reset: () => dispatch(reset())
  }
}
```

mapDispatchToProps 함수의 반환 값에 일일이 함수형태로 만들어서 dispatch로 감싸서 리턴하는 것은 꽤나 번거로운 작업이다. 특히 디스패치할 액션들이 수십개, 수백개가 된다면 말이다.

이때 bindActionCreators라는 리덕스에서 만들어 놓은 함수를 이용하면 조금 더 편하게 mapDispatchToProps 함수를 작성할 수 있다.

```js
import { bindActionCreators } from 'redux'

function mapDispatchToProps(dispatch) {
  return bindActionCreators({ increment, decrement. reset }, dispatch)
}

```
위의 bindActionCreators 함수는 첫번째 인자로 액션생성함수들이 담겨있는 객체를 받고, 두번째 인자로 dispatch를 받는다.

반환 값은 아래와 같다.
```js
{
increment: (...args) => dispatch(increment(...args)),
decrement: (...args) => dispatch(decrement(...args)),
reset: (...args) => dispatch(reset(...args)),
}
```

mapDispatchToProps 함수 작성이 한결 편해졌다.

하지만 사실 이 방법 보다도 더 좋은 방법이 한가지가 있다. 
바로 mapDispatchToProps를 함수가 아닌 객체로 만드는 것이다.

#### Object Shorthand Form of mapDispatchToProps

```js
const mapDispatchToProps = { increment, decrement, reset}
```

이렇게 하면 리덕스가 내부적으로 bindActionCreators를 실행하는데 이때 mapDispatchProps 객체를 첫번째 인자로 받고, 두번째 인자로 dispatch를 받는다. 이 과정은 자동으로 진행되기 떄문에 따로 필요한 설정이 없다.

mapDispatchToProps를 객체형태로 쓰는 것은 함수형태로 쓸때보다 코드가 훨씬 간결하고 한눈에 들어온다는 장점이 있다.

이렇게 객체형태의 mapDispatchToProps를 object shorthand form이라고 한다. 

>**리액트 리덕스 공식문서에선 특별히 다른 이유가 없는 한 object shorthand form을 쓰는 것을 추천하고 있다.**

---
#### P.S. (postscript/afterthought)  
얼마 전 내 프로젝트 중 하나를 다시 들여다 보았다. 그 프로젝트 안에서 mapDispatchToProps의 코드를 보던 중 이해하기가 벅찼었다.  
그렇게 내가 작성했던 코드를 이해하는 과정에서 배운 것들을 블로그 포스팅을 통해 정리하게 된 것이다.  
프로젝트 진행 시 코드를 들여다보니 나는 꽤나 리덕스를 깊게 공부하며 도전적으로 코드를 써본 것 같다.  
단지 시간적 여유가 없어서 정리가 조금 부족했었던 것 같다.  
더군다나 redux thunk(썽크)라는 리덕스 미들웨어까지 사용해서 작성했기 때문에 이해하기까지 애를 좀 먹었다.  
하지만 덕분에 내가 리덕스에 관해 아는 것과 모르는 게 무엇인지 분별하고, 더 나아가 내용을 정리해서 확실하게 내 것으로 만들었던 계기가 된 것 같다.

다음 포스팅은 *redux thunk*에 관한 내용을 다뤄볼 계획이다.
