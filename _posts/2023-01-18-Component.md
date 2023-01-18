---
layout: single
title: "Component와 Props"
categories:
    - React
tag: [Component, Props]

toc: true
toc_sticky: true
---


'Component'의 개념
---

&nbsp; 리액트는 **component 기반의 구조**이다.

리액트는 모든 페이지가 component로 구성되어 있고,  
하나의 component는 또 다른 여러개의 component의 조합으로 구성될 수 있다.  

리액트는 component 기반의 구조라고 부르는 이유는  
작은 컴포넌트들이 모여서 하나의 component를 구성하고,  
이러한 component들이 모여서 전체 페이지를 구성하기 때문이다.
<br/><br/>

리액트 component는 개념적으로 js의 함수와 비슷하다.  
**함수가 입력을 받아 출력을 뱉는 것 처럼 component도 입력을 받아 정해진 출력을 내뱉는다.**  
그래서 리액트 component를 하나의 함수라고 생각하면 개념적으로 쉽다.

하지만 리액트의 component의 입력과 출력은 일반적인 js함수와는 조금 다르다.  
리액트 component의 **입력은 props**가 되고, **출력은 react element**가 된다.

결국 리액트 component의 역할은 어떠한 속성들을 입력으로 받아 그에 맞는 리액트 element를 생성하여 return해주는 것이다.

리액트 element는 리액트 앱을 구성하는 가장 작은 단위이고,  
js객체 형태로 화면에 보이는 것을 기술한다.

**리액트 component는 만들고자 하는대로 props를 넣으면, 
해당 속성에 맞춰 화면에 나타날 element를 만들어주는 것이다.**

붕어빵 틀을 component라고 생각하면 편하다.  
완성된 붕어빵들은 리액트 element이다.
이 과정은 객체지향의 class라는 틀에서 instance 붕어빵이 나오는 개념과도 비슷하다.
<br/><br/>



'props'란?
---

&nbsp; 리액트 component에 입력으로 들어가는 props란

property라는 속성, 특성이라는 뜻을 가진 영어단어를 줄여서 props라고 쓴다.

리액트에서는 속성이라는 뜻으로 사용되고,  
리액트 component의 속성을 의미한다. 

props는 붕어빵에 들어가는 재료이다.  
같은 붕어빵이라도 어떤 재료를 넣느냐에 따라 다른 맛이난다.  
모양은 같은 붕어빵이지만 속을 뜯어보면 안에 들어있는 재료, 색이 다른 것처럼  
props는 같은 component에서 눈에 보이는 글자나 색등의 속성을 바꾸고 싶을 때 사용하는 component의 속 재료라고 생각하면 됨

props는 component에 전달할 다양한 정보를 담고 있는 js객체이다.  
우리가 component에 어떤 데이터를 전달하고,  
전달된 데이터에 따라 다른 모습의 element를 화면에 렌더링 하고 싶을 때  
해당 데이터를 props에 넣어서 전달한다.
<br/><br/>



props의 특징
---

&nbsp; props의 특징은 read-only 즉, 읽기 전용이다.  
읽을 수만 있다는 것은 **값을 변경할 수 없다**는 말이다.

props의 값은 component가 element를 생성하기 위해 사용하는 값이다.  
그런데 이 값들이 element를 생성하는 도중에 갑자기 바뀌면 제대로 된 element가 생성될 수 없다.

그렇다면 다른 props의 값으로 element를 생성하려면 어떻게 해야할까?  
새로운 값을 component에 전달하여 새로 element를 생성하면 된다.  
이 과정에서 element가 다시 렌더링 되는 것이다.
<br/><br/>

모든 리액트 component는 그들의 props에 관해서는 pure함수 같은 역할을 해야한다.

쉽게 말해,  
모든 리액트 component는 props를 직접 바꿀 수 없고,  
같은 props에 대해서는 항상 같은 element를 보여줘야 한다.
<br/><br/>



'props'의 사용법
---

&nbsp; props는 component에 전달할 다양한 정보를 담고 있는 js객체이다.
```js
function App(props) {
    return (
        <Profile
            name="이현수"
            age={28}
        />
    )
}
```
JSX를 사용하는 경우 키와 값의 형태로 component에 props를 넣을 수 있다.  
**props에 값을 넣을 때에는 문자열 이외에도 정수, 변수, 다른 컴포넌트등이 들어갈 수 있다.**
이때에는 중괄호{}를 사용해서 감싸주어야 한다. 

JSX를 사용하는 경우에는 간단하게 props를 넣을 수 있다.
JSX를 사용하지 않는 경우에는 createElement() **`두번째 파라미터`**에 js객체를 넣으면 된다.
```js
React.createElement(
    Profile,
    {
        name="이현수",
        age=28
    },
    null
)
```
<br/><br/>



'component' 만들기
---

&nbsp; 리액트 component는 **class component**와 **function component**로 나뉜다.

리액트 초기버전에서는 class component를 주로 사용했다.  
하지만 현재는 함수 component를 개선해서 주로 사용한다.  
함수 component를 개선하는 과정에서 개발된 것이 Hook이다.  

앞에 말한 "모든 리액트 component는 pure함수같은 역할을 해야한다."라는 말은 리액트 component를 일종의 함수라고 생각한다는 뜻이다.

```js
function Welcome(props) {   // 함수 컴포넌트
    return <h1>안녕, {props.name}</h1>
}
```
이 함수의 경우 하나의 props객체를 받아 리액트 element를 return 하기 때문에,  
리액트 component라고 할 수 있다.

이렇게 생긴 것을 함수 component라고 부른다.  
함수 component는 이처럼 간단한 코드를 장점으로 가진다.
<br/><br/>


클래스 컴포넌트란 js es6의 class를 사용해서 만들어진 형태의 component이다.  
class component는 함수 component에 비해 생명주기 같은몇가지 추가적인 기능을 가지고 있다.

```js
class Welcome extends React.Component {
    render () {
        return <h1>안녕, {this.props.name}</h1>
    }   // 클래스 컴포넌트
}
```
리액트 모든 class component는 react.component를 상속받아 만든다.
<br/><br/>



자잘한 'component'의 특징
---

&nbsp; **component의 이름은 항상 대문자로 시작해야 한다.**
리액트는 소문자로 시작하는 component를 DOM 태그로 인식하기 때문이다.  
<br/>

**component 합성은 여러개 component를 합쳐서 하나의 component를 만드는 것이다.**

이와 반대로 복잡한 component를 쪼개서 여러개의 component 나눌 수 있다.
<br/><br/>

**큰 component에서 일부를 추출해서 새로운 component를 만들 수 있다.**

component추출을 잘 활용하게되면 component의 재사용성이 올라간다.  
component가 작아질수록 기능과 목적이 명확해지고, props도 단순해지기 때문이다.  
또한, 다른 곳에서 사용할 수 있는 확률이 올라가며, 개발속도도 향상된다.  
참고로, 추출 시 재사용성 측면을 고려하여, 보편적인 단어를 사용해야 한다.
<br/><br/>



생각정리
---

&nbsp; component를 다른 프로젝트에서 재사용을 하는 경우가 있을까??,,,

-------------------------

감사한 참조
* https://www.inflearn.com/course/처음-만난-리액트
