<h2>useState와구조분해할당</h2>

자바스크립트 공부할때 구조분해할당을 어디에, 왜 써먹는지 몰랐는데 useState를 쓸때 멋도 모르고 쓰던게 구조분해 할당이었음

=> 일단 구조분해 할당은
```
객체나 배열에 저장된 데이터 전체가 아닌 일부만을 필요로하는 경우가 생기는데,
이때 객체나 배열을 변수로 분해할 수 있게 해주는 것
이외에도 함수의 매개변수가 많거나 매개변수 기본값이 필요한 경우등에서 사용함

// 이름과 성을 요소로 가진 배열
let arr = ["Bora", "Lee"]

// 구조 분해 할당을 이용해
// firstName엔 arr[0]을
// surname엔 arr[1]을 할당하였습니다.
let [firstName, surname] = arr;

alert(firstName); // Bora
alert(surname);  // Lee

```

=> 리액트에서는 useState를 사용할때 구조분해할당을 사용함

```
문법적으로 보면 아래 예시의 isChecked, setIsChecked 는 useState 의 리턴값을 구조 분해 할당한 변수임.

function CheckboxExample() {
  const [isChecked, setIsChecked] = useState(false);
}
[코드] useState 문법 예시

function CheckboxExample() {
  // 1번 코드를 풀어쓰면
  const [isChecked, setIsChecked] = useState(false); // 1번

  //...

  // 2번 코드와 같습니다.
  const stateHookArray = useState(false); // 2번
  const isChecked = stateHookArray[0];
  const setIsChecked = stateHookArray[1];
}
[코드] useState 구조 분해 할당 예시


useState 를 호출하면 배열을 반환하는데, 
배열의 0번째 요소 === 현재 state 변수
1번째 요소 === 이 변수를 갱신할 수 있는 함수 
useState 의 인자로 넘겨주는 값 === state의 초깃값


const [state 저장 변수, state 갱신 함수] = useState(상태 초기 값);
```
