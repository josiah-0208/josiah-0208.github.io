---
layout: single
title: "useCallback() - 랜더링 되게 하지마!"
categories:
  - React
tag: 
  - useCallback

toc: true
toc_sticky: true
---

Memoization
---

&nbsp; 'Memoization'이란,

동일하거나 비슷한 계산을 반복해야 할 때,

**결과값을 저장해 놓아,  
불필요한 반복 수행을 막는** 개념이다
<br/><br/>



'useMemo()'와 useCallback()'의 개념
---


&nbsp; useMemo()와 useCallback()은 `memoization`의 개념을 사용한다.

* useMemo()는 **연산의 결과를 저장**해둔다.  
  컴포넌트의 결과값(화면)을 저장할 수도 있다.
* useCallback()는 **함수를 저장해 두고**,  
  함수가 재생성되지 않게 한다.
<br/><br/>


```js
const memoizedCallback = useCallback(function, deps);
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```  


매개변수 `첫 인자`로,  
useMemo는 **연산의 결과값**을  
useCallback은 **함수 그 자체**를 받는다.

`두 번째 인자`로는,  
둘 다 *의존성 배열*을 받는다.
<br/><br/>



사용하는 이유
---

&nbsp; 최적화를 위해서이다.

useMemo()는 연산량이 많은(비용이 큰) 작업의 결과를 저장해두어,  
**방대한 연산이 반복 수행되는 것을 막을 수 있다**.
<br/><br/>

useCallback()은 **리랜더링을 줄일 수 있다**.

이에 대하여 자세히 알아보자.

먼저, React가 **`리렌더링을 하는 경우`**는 4 가지이다.

    1. 자신의 state가 변경될 때
    2. 부모로부터 받은 props가 변경될 때
    3. 부모가 리렌더링 될 때
    4. forceUpdate() 를 실행하였을 때

위 조건들을 염두에 두고, useCallback의 필요성을 생각해보자.

먼저, **리액트의 함수 컴포넌트**는 **js의 함수**와 모양과 기능이 거의 같아,  
return 값으로 리액트 엘리먼트(element)를 반환한다.

리액트 엘리먼트는 JS의 객체의 형태이고,  
**엘리먼트는 '불변'이므로 컴포넌트에 의해 다시 생성된다**.

따라서, 해당 컴포넌트의 모든 객체들은 다시 생성된다.

그런데 이때 중요한 것은,  
다시 생성된 객체들은 **'값이 같더라도 다른 객체로 취급'**이 된다.  
(reference type이므로, 참조하는 주소가 달라지기 때문에)

리액트는 이를 변화로 인식하고, 리랜더링을 수행한다.   
useMemo와 useCallback을 사용하면 이러한 리랜더링을 방지할 수 있다.
<br/><br/>



생각 정리
---

최적화를 위해 사용하는 개념이 적재적소에 사용되지 않는다면,  
더 많은 비용이 들 수 있겠다.
useMemo, useCallback 자체가 연산일테니,  
* https://yceffort.kr/2022/04/best-practice-useCallback-useMemo#props의-참조-동일성은-언제-문제가-될까  

여기에 잘 정리되어 있다. 나중에 다시 한 번 보자.

리액트를 오래 한 것은 아니지만,  
알아갈수록 사용자에게 가게되는 파일이  
최적화가 잘된 상태가 되면 좋겠다는 생각이 든다.

하지만 알아야 할 것들이 투성이인 것 같다,,,

비록 해당 개념이 낮은 단계의 최적화겠지만, 남용해서도 안되고,  
이렇게 하나하나 신경을 쓰다보면 완성도가 높은 페이지를 사용자에게 건네줄 날이 오지 않을까?
<br/><br/>


------------------------------------


감사한 참조*
* https://espania.tistory.com/m/368
* https://leego.tistory.com/entry/React-useCallback과-useMemo-제대로-사용하기


