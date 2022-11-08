```
let arr = [10, 30, 40, 20]
let value = Math.max(arr) //NaN이 나옴
```

```
let arr = [10, 30, 40, 20]
let value = Math.max(...arr) //40
```
배열을 그냥 집어넣으면 안되고 spread문법을 사용하여 하나하나 풀어서 넣어주어야함
배열을 인자로 넣을때 spread가 아주 유용함

```
let fruits = ['apple', 'banana', 'grape'];
let vegetables = ['tomato', 'pumpkin'];

let copiedFruits = [...fruits];
copiedFruits.push('pineapple');

let basket = [...fruits, ...vegetables]

console.log(basket)//['apple', 'banana', 'grape', 'tomato', 'pumpkin']
```
copiedFruits는 fruits를 복사한 배열입니다. 그러나 spread 문법은 기존 배열을 변경하지 않으므로(immutable),
copiedFruits를 수정하다고 해서 fruits가 함께 수정되지 않습니다.


