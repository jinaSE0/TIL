```
let name = '김코딩';

function showName() {
  let name = '박해커'; // 지역 변수
  console.log(name); // 두 번째 출력 박해커
}

console.log(name); // 첫 번째 출력 김코딩
showName();
console.log(name); // 세 번째 출력 김코딩
```

- 첫번째와 세번째는 김코딩인 이유; 지역변수에 선언된 name변수는 안쪽 스코프이르모 접근불가
- 두번째 출력은 변수이름이 전역변수와 같지만 지역 변수가 전역 변수보다 우선순위가 높으므로 지역변수 name이 출력됨
- 동일한 변수 이름으로 인해 바깥쪽 변수가 안쪽 변수에 의해 가려지는 현상을 쉐도잉이라고함

```
let name = '김코딩';

function showName() {
  name = '박해커';
  console.log(name); // 두 번째 출력 박해커 -> 전역변수 name에 박해커라는 값이 할당됨
}

console.log(name); // 첫 번째 출력 김코딩
showName();
console.log(name); // 세 번째 출력 박해커
```

- 위 코드랑 다른 점은 함수안에서  let으로 선언하지 않음

<h2>스코프의 종류</h2>
- 블록 < 로컬 < 글로벌
- 중괄호로 둘러싼 범위, **화살표 함수로 둘러싼 범위** : 블록 스코프
  - 블록스코프안에서 let으로 정의된 변수는 블록 범위를 벗어나는 즉시 접근 불가
  - 만약 var로 선언했다면 블록 범위를 벗어나도 같은 펑션 스코프 안이었다면 사용가능함
  - var는 블록스코프를 무시하고 함수 스코프만 따름(화살표함수의블록스코프는 무시하지않음)
- 함수로 둘러싼 범위 : 함수 스코프
- 함수 스코프는 함수의 실행부터 종료까지이고, var 선언은 함수 스코프의 최상단에 선언됩니다. <br>
- 선언 키워드 없는 선언은 최고 스코프에 선언됩니다.<br>
- 함수 내에서 선언 키워드 없는 선언은, 함수의 실행 전까지 선언되지 않은 것으로 취급합니다.
- strict mode를 사용하면 ‘선언 없는 변수 할당’을 브라우저가 에러로 처리하기 때문에 side effect를 방지할 수 있습니다.


```
function greetSomeone(firstName) {
  var time = "night";
  if (time === "night") {
    var greeting = "goodnight";
  }
  return greeting + " " + firstName;
}
greetSomeone("Steve"); //goodnight Steve출력

```

```
function greetSomeone(firstName) {
  let time = "night";
  if (time === "night") {
    let greeting = "goodnight";
  }
  return greeting + " " + firstName;
}
greetSomeone("Steve"); //greeting을 찾을 수 없어 레퍼런스 에러가 남
```
