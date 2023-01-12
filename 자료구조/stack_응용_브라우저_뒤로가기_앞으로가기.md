stack_응용_브라우저_뒤로가기_앞으로가기
---
stack을 활용해서 브라우저 뒤로가기와 앞으로 가기를 구현해봄...

```
function browserStack(actions, start) {
  let prev = []
  let current = start
  let next = []

  if(typeof start!=="string") return false
  
  for(let el of actions){
    //문자열이면 하나씩 prev에 들어가고
    if(typeof el==="string"){
      prev.push(current)
      current=el
      next = []
    }
    //-1 뒤로가기니까 current에 있던거는 next로, prev에서 pop해서 current에, 
    if(el===-1&&prev.length>0){

      next.push(current)
      current = prev.pop()
    }
    //1이면 앞으로가기니까 next에서 마지막에 있는걸 current
    if(el===1&&next.length>0){
      prev.push(current)
      current = next.pop()
    }
  }
  return [prev, current, next]

}
//행동한 순서가 들어있는 배열 actions와 시작 페이지 start가 주어짐, 특정한 페이지는 문자열이고  뒤로가기는 -1 앞으로가기는 1 
//마지막에 접속해 있는 페이지 && 방문했던 페이지들이 담긴 스택을 반환하는 솔루션
//return [prev, current, next]
```
