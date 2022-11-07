<h2>객체의 브라켓 노테이션</h2>

그냥 dot notation 쓰면되지 브라켓노테이션은 언제쓰나요?
- 키값이 동적으로 변할때 키값이 변수일때 
- 매개변수가 달라져도 그때 그때 원하는 것을 출력할 수 있음


```
function getAgeOrName(obj, ageOrName){
  return obj[ageOrName] //평소 브라켓 노테이션 쓸때처럼 ""를 쓰지않음으로써 이렇게 동적으로 변하는 상황에 대응할 수 있음
}

let output = getAgeOrName(person, "name")
let output2 = getAgeOrName(person, "age")
```

- dot notatoion과 똑같이 쓰려면 "문자열"로 기입
```
tweet["content"] === tweet.content; //true
```

- dot/ bracket notation을 통해 값을 추가할 수도 있다. 
- in연산자이용해서 해당하는 키가 있는지 확인가능하다 <br>
```"키" in 객체변수명//true나 false나옴```
