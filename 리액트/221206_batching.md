리액트 배칭(batching)
---
리액트가 더 나은 성능을 위해 여러 개의 state업데이트를 하나의 리렌더링으로 묶는것을 말함 <br>
예를들어 하나의 클릭 이벤트 안에 두개의 state업데이트를 가지고 있으면 리액트는 이 작업을 배칭하여 하나의 리렌더링을 만든다 
- 리액트17에서는 입벤트핸들러와 유즈 이펙트에 배칭기능을 지원하고
- 18에서는 프로미스 내부나  setTimeout에도 지원함

아래와 같이 이벤트 핸들러에 카운트의상태가 변경되는 함수가 있다고 하자

```
const [count, setCount] = useState(0)

//동기적인 코드인데 batching이 되면서 비동기적으로 된다고 생각해야함 
const eventHandler=()=>{
  //1. 갱신의 취소
  setCount(count+1) // coount가 0을 계속 바라보고있다고 생각하면됨
  setCount(count+1)
  setCount(count+1) 
  // 이렇게 코드가 있다면 과연 결과값은 어떻게 될까? -> 1이 나옴
  
  //2. 
  setCount(count+1)
  setCount(count+2)
  setCount(count+3) //3이 나옴
  
  //3. 함수형 업데이트
  setCount((prev)=> prev+1)
  setCount((prev)=> prev+1)
  setCount((prev)=> prev+1) // 3이 나옴
  //왜냐하면 콜백함수의 인자는 갱신된 값을 부르기때문
  
  //4. 함수형 업데이트
  setCount((prev)=> prev+1)
  setCount((prev)=> prev+2)
  setCount((prev)=> prev+3) //6이 나옴
  
}

//이하 코드 생략
```

[읽어보자](https://tasoskakour.com/blog/react-18-automatic-batching)
