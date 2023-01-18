---
layout: single
title: "Component & Props"
categories:
    - React
tag: 
    - Component

toc: true
toc_sticky: true
---


리액트는 component 기반의 구조이다.

리액트는 모든 페이지가 component로 구성되어 있고,
하나의 component는 또 다른 여러개의 component의 조합으로 구성될 수 있다.

마치 레고블록을 조립하듯이 끼워 맞춰 새로운 component를 만들 수 있다.

리액트는 component 기반의 구조라고 부르는 이유는 
작은 컴포넌트들이 모여서 하나의 component를 구성하고
이러한 component들이 모여서 전체 페이지를 구성하기 때문에

하나의 component를 반복적으로 사용함으로써 전체 코드의 양을 줄일 수 있으므로
자연스레 개발 시간과 유지보수 비용을 줄일 수있다.

리액트 component는 개념적으로는 js의 함수와 비슷
함수가 입력을 받아 출력을 뱉는 것 처럼 리액트 component도 입력을 받아 정해진 출력을 내뱉는다.
그래서 리액트 component를 하나의 함수라고 생각하면 개념적으로 쉽다.

하지만 리액트의 component의 입력과 출력은 일반적인 js함수와는 조금 다르다.

리액트 component의 입력은 props가 되고, 출력은 리액트 element가 된다.

결국 리액트 component의 역할은 어떠한 속성들을 입력으로 받아 그에 맞는 리액트 element
를 생성하여 return해주는 것

리액트 element는 리액트 앱을 구성하는 가장 작은 빌딩 블록들이라고 배움
js객체 형태로 존재하며 화면에 보이는 것을 기술한다.
리액트 component는 만들고자 하는대로 props를 넣으면
해당 속성에 맞춰 화면에 나타날 element를 만들어주는 것

붕어빵 기계틀을 component라고 생각하면 편함 붕어빵들은 리액트 element
이 과정은 객체지향의 class라는 틀에서 instance 붕어빵이 나오는 개념도 비슷함


리액트 component에 입력으로 들어가는 props란

props는 property라는 속성, 특성이라는 뜻을 가진 영어단어를 줄여서 쓴 것
리액트에서는 속성이라는 뜻으로 사용됨
리액트 component의 속성 

props는 붕어빵에 들어가는 재료를 의미
같은 붕어빵이라도 어떤 재료를 넣느냐에 따라 다른 맛이남.
모양은 같은 붕어빵이지만 속을 뜯어보면 안에 들어있는 재료, 색이 다름
이처럼 props는 같은 react컴포넌트에서 눈에 보이는 글자나 색등의 속성을 바꾸고 싶을 때
사용하는 component의 속 재료라고 생각하면 됨

componenent의 모습과 속성을 결정하는 것이 props
props는 component에 전달할 다양한 정보를 담고 있는 js객체
우리가 component에 어떤 데이터를 전달하고 전달된 데이터에 따라 다른 모습의 element를 화면에
랜더링 하고 싶을 때 해당 데이터를 props에 넣어서 전달

props의 특징
---
props의 중요 특징은 read-only 읽기 전용이다.
읽을 수만 있다는 것은 값을 변경할 수 없다는 말
props의 값은 리액트 component가 element를 생성하기 위해 사용하는 값
그런데 이 값들이 element를 생성하는 도중에 갑자기 바뀌면 제대로 된 element가 생성될 수 없음

그렇다면 다른 props의 값으로 element를 생성하려면 어떻게 해야할까
새로운 값을 component에 전달하여 새로 element를 생성하면 됨
이 과정에서 element가 다시 랜더링 되는 것

pure한 함수 = 입력값을 변경하지 않으며, 같은 입력값에 대하여 항상 같은 출력값을 return한다는 뜻
모든 리액트 component는 그들의 props에 관해서는 pure함수 같은 역할을 해야한다.

모든 리액트 component는 props를 직접 바꿀 수 없고, 같은 props에 대해서는 항상 같은 element를 보여줄 것

props사용법
---

props가 component에 전달할 다양한 정보를 담고 있는 js객체
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
JSX를 사용하는 경우 component 키와 값 쌍의 형태로 component에 props를 넣을 수 있음
props에 값을 넣을 때에도 문자열 이외에 정수, 변수, 다른컴포넌트등이 들어갈 때에는
{}를 사용해서 감싸주어야 한다. 

JSX를 사용하는 경우에는 간단하게 props를 넣을 수 있다.
JSX를 사용하지 않는 경우에는 createElement() 두번째 파라미터에 js객체를 넣으면 된다.
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

component 만들기
---
리액트 component는 크게 class component와 함수 component로 나뉨
리액트 초기버전에서는 class component를 주로 사용
하지만 이후에는 함수 component를 개선해서 주로 사용
함수 component를 개선하는 과정에서 개발된 것이 Hook이다.

# function component
모든 리액트 component는 pure함수같은 역할을 해야한다.
이 말은 리액트 component를 일종의 함수라고 생각한다는 뜻

```js
function Welcome(props) {
    return <h1>안녕, {props.name}</h1>
}
```
이 함수의 경우 하나의 props객체를 받아 리액트 element를 return 하기 때문에
리액트 component라고 할 수 있음. 이렇게 생긴 것을 함수 component라고 부름
함수 component는 이처럼 간단한 코드를 장점으로 가짐.

## class component
js es6의 class를 사용해서 만들어진 형태의 component
class component는 함수 component에 비해 생명주기 같은몇가지 추가적인 기능을 가지고 있다.

```js
class Welcome extends React.Component {
    render () {
        return <h1>안녕, {this.props.name}</h1>
    }
}
```
위 함수 component와 동일한 역할을 하는 class component
리액트 모든 class component는 react.component를 상속받아 만든다는 것

component의 특징
---
component의 이름은 항상 대문자로 시작해야함
리액트는 소문자로 시작하는 component를 DOM 태그로 인식하기 때문에

component 합성
component 합성은 여러개 component를 합쳐서 하나의 component를 만드는 것
리액트에서는 component안에 또 다른 component를 사용할 수 있기 때문에
복잡한 화면을 여러개 component로 나누어 구현 가능
이와 반대로 복잡한 component를 쪼개서 여러개의 component 나눌 수 있음
큰 component에서 일부를 추출해서 새로운 component를 만든다는 뜻
component추출을 잘 활용하게되면 component의 재사용성이 올라간다.
왜냐면 component가 작아질수록 기능과 목적이 명확해지고, props도 단순해지기 때문에
다른 곳에서 사용할 수 있는 확률이 올라감. 동시에 개발속도도 향상됨
추출 시 보편적인 단어를 사용해야 재사용성 측면을 고려 가능
의미상 큰 차이없이