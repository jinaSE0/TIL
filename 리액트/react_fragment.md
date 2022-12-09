리액트 프레그먼트 하는 이유
---

- 리액트는 하나의 컴포넌트만을 리턴할 수 있음
- 고로 리턴문 안에는 반드시 하나의 최상위 태그가 있어야함

```
만약에
<div>와 같은 걸로 감싸주게되면
최종적으로 보여지는 html에서 의미없는 div를 볼 수 있게된다
```
```
이를 방지하기 위해
리액트 프레그먼트를 씀
<Fragment> </Fragment> 또는 <> </> 
```

[참고한 블로그](https://velog.io/@lilyoh/React-Fragments-%EC%82%AC%EC%9A%A9%EC%9D%B4%EC%9C%A0-%EB%B0%8F-%EC%82%AC%EC%9A%A9%EB%B2%95)
