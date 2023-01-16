---
layout: single
title: "useCallback() - 함수를 다시 만들지마!"
categories:
  - React
tag: 
  - useCallback

toc: true
toc_sticky: true
---

Memoization
---

memoization이란
동일하거나 비슷한 계산을 반복해야할 때 결과값을 저장해둬서
불필요한 반복 수행을 하지 않아도 되는 개념이다

'useCallback()'의 개념
---



usecallback 또한, memoization 개념을 사용한다.

비슷하게 useMemo()가 있다.,
<br/><br/>



'useCallback()'을 사용하는 이유
---

&nbsp; 부모 컴포넌트에서 함수가 재생성되면,
랜더링이 되면
만약 자식 컴포넌트에 prop으로 함수를 준다면
재생성된 함수로 인해
자식 컴포넌트가 불필요하게 재랜더링이 될 수 있다.
useCallback으로 함수를 생성하지 않는다면

그래서 최적화
함수

<br/><br/>



생각 정리
---

리액트를 많이 한건 아니지만,
할때마다
사용자에게 건네주는 파일이
정말 최적화가 잘된 형태로 가꾸고 싶다는 생각을 했다.

비록 낮은 단계의 최적화지만
하나하나 신경을 쓰다보면
완성도가 높은 파이지를 사용자에게 건네줄 수 있게 되겠지?
