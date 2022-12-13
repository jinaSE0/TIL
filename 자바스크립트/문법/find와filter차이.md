find
- find 함수는 배열 원소에 대해서 주어진 함수연산을 하다가 함수가 true를 반환하면 find함수도 같이 종료됩니다. 
- find함수로 조건에 만족하는 원소를 반환하지 못하는 경우 undefined 를 반환합니다.

filter
- filter 함수는 각각 배열의 원소에 대해서 전달받은 함수의 결과가 true를 반환한 원소들로만 배열을 만듭니다.

```

let arr = [
  { name : 'dog', color: 'white' },
  { name : 'dog', color: 'black' },
  { name : 'cat', color: 'white' }
]

arr.find(el => el.color === 'white')
// { name: 'dog', color: 'white' }
// 찾자마자 

arr.filter(el => el.color === 'white')
// { name: 'dog', color: 'white' }
// { name : 'cat', color: 'white'}
// 리턴되는게 하나일때도 배열로 나옴
```

[참고한 블로그](https://humahumahuma.tistory.com/83)
