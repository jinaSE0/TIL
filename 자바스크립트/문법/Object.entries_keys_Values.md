------------Object.entries()--------------
```
const object1 = {
  a: 'somestring',
  b: 42
};

for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`); 
  //왜 객체인데 for of 문법을 쓸 수 있을까 => Object.entries를 사용하면 배열형태로 리턴하기때문
  //그래서 const다음에 배열형태로 입력
}

// expected output:
// "a: somestring"
// "b: 42"
```
-------------Object.keys()---------------
```
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.keys(object1));
// expected output: Array ["a", "b", "c"]
```

-------------Object.Values()---------------
```
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.values(object1));
// expected output: Array ["somestring", 42, false]
```
