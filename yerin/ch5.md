## 진화된 함수형 컴포넌트: 리액트 훅



리액트 훅이란? 함수형 컴포넌트에서도 컴포넌트의 상탯값을 관리할 수 있고, 생명 주기 함수를 이용할 수 있도록 함.

-로직을 재사용하는 기존 방식의 한계

-클래스형 컴포넌트의 한계

는 훅을 이용하면 개선할 수 있다.

**훅의 장점 **

- 재사용 가능한 로직을 쉽게 만들 수 있다.
- 가독성이 좋아짐
- 정적 타입 언어로 타입을 정의하기 쉬움



**훅의 기본**

- useState

  기본적으로 ` const [name, setName] = usesState('')` 이런식으로 사용하고

  ` const [state,setState] = useState({name:'',age:''})`이런식으로 하나의 객체에 담아서 사용할 수 있다.

  하나의 객체에 담아서 사용할 경우 상태값을 변경할 때 이전 상태값을 지움으로 `...state,` 와 같은 코드로 상태값을 유지해줘야한다.

  [useState 4가지 사용 방법](https://medium.com/@shlee1353/리액트-hooks-usestate-4가지-상용방법-dfe8b2096750)

- useEffect

  렌더링 결과가 실제 돔에 반영된 후 호출된다.

  * Api호출
  * 이벤트 처리 함수 등록 해제
  * 로직별로 코드 모으기

  [useEffect에 대한 짧은 가이드](https://velog.io/@jepjap93/useEffect에-대한-짧은-가이드)



**훅 사용 시 지켜야 할 규칙**

1. 하나의 컴포넌트에서 훅을 호출하는 순서는 항상 같아야 한다.

   -> 리액트는 내부적으로 배열로 훅을 관리하기 때문

2. 훅은 함수형 컴포넌트 또는 커스텀 훅 안에서만 호출되어야 한다.



**리액트의 다양한 훅 살펴보기**

* useContext : Consumer 컴포넌트 없이 콘텍스트 사용하기

* usesRef : 함수형 컴포넌트에서 돔 요소 접근하기

* useMemo, useCallback : 메모이제이션 훅

* useReducer : 컴포넌트의 상탯값을 리덕스처럼 관리하기

* useImperativeHandle : 부모 컴포넌트에서 접근 가능한 함수 구현하기

* useLayoutEffect : 렌더링 결과가 돔에 반영된 후 동기로 호출

  useEffect는 비동기로 호출된다

* useDebugValue : 커스텀 훅의 내부 상태를 관찰할 수 있다.



**클래스형 컴포넌트와 훅**

* componentDidMount, componentWillUnMount 메서드는 useEffect 또는 useLayoutEffect 훅으로 대체할 수 있다.
* 클래스 멤버 변수는 useRef 훅으로 대체할 수 있다.
* constructor 메서드는 useRef훅을 이용하여 만들 수 있다.
* componentDidUpdate 또한 useRef로 이전 상태값을 저장하여 update를 확인한다.
* forceUpdate 메서드는 useReducer을 이용하여 상태값을 바꾸어 강제로 랜더링을 한다,