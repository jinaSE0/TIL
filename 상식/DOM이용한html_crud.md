<h2>DOM이용한html_crud</h2>

- DOM은 Document Object Model의 약자로, HTML 요소를 Object(JavaScript Object)처럼 조작(Manipulation)할 수 있는 Model.

```
Create 새로운 돔 객체 만들기
const tweetDiv = document.createElement('div')//div가 생성되어서 변수에 저장됨
Append 기존의 돔 객체에 붙이기
document.body.append(tweetDiv)//바디에 tweetDiv를 붙임(트리구조와 연결)
```
- DOM으로 HTML 엘리먼트의 정보를 조회하기 위해서는 querySelector의 첫 번째 인자로 셀렉터(selector)를 전달하여 확인할 수 있습니다. 
- 셀렉터로는 HTML 요소("div"), id("#tweetList"), class(.tweet) 세 가지가 가장 많이 사용됩니다.

```
Read 돔객체를 선택해서 조회하기
const oneTweet = document.querySelector('.tweet')
const tweets = document.querySelectorAll('.tweet')

const getOneTweet = document.getElementById('container')//쿼리셀렉터의 옛날 방식
const queryOneTweet = document.querySelector('#container')
console.log(getOneTweet === queryOneTweet) // true

const container = document.querySelector('#container')
const tweetDiv = document.createElement('div')
container.append(tweetDiv)//콘테이너의 맨 마지막 자식 요소로 tweetDiv추가됨
```

```
Update
oneDiv.textContent = 'dev'; 
console.log(oneDiv) // <div>dev</div> 

```

```
Delete
const container = document.querySelector('#container')
const tweetDiv = document.createElement('div')
container.append(tweetDiv)
tweetDiv.remove() // 이렇게 append 했던 요소를 삭제할 수 있다.

container의 모든 자식 요소 지우기
document.querySelector('#container').innerHTML = '';
-> 보안에서 몇 가지 문제를 가지고 있음
-> 그래서 아래와 같이 자식요소를 지정해서 삭제하는 메서드로 반복문을 돌리는 것이 좋다
const container = document.querySelector('#container');
while (container.firstChild) {
  container.removeChild(container.firstChild);
}
-> 지우고 싶지않은 자식요소가 있다면
자식 요소가 담고 있는 문자열을 비교해 조건문을 원하는 것만 남길 수 있게 만들거나, 
새로운 변수를 생성하고 Tweet List를 할당해뒀다가 반복문이 끝난 뒤에 새롭게 추가한다든지 그런 방법을 생각해보자
```

- 다른 attribute를 추가하는 법 : setAttribute 
- https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute
- 엘리먼트의 입력값을 설정하거나 얻어낼때 쓰는 속성 : 해당 엘리먼트를 querySelector 등을 이용해 가져온 후 value라는 속성으로 접근

