<h2>event.target과버블링</h2>

```
// Make a list
const ul = document.createElement('ul');
document.body.appendChild(ul);

const li1 = document.createElement('li');
const li2 = document.createElement('li');
ul.appendChild(li1);
ul.appendChild(li2);

function hide(evt) {
  // evt.target refers to the clicked <li> element
  // This is different than evt.currentTarget, which would refer to the parent <ul> in this context
  evt.target.style.visibility = 'hidden';
}

// Attach the listener to the list
// It will fire when each <li> is clicked
ul.addEventListener('click', hide, false);
```
- https://developer.mozilla.org/en-US/docs/Web/API/Event/target

위에서 분명히 이벤트를 건 것은 ul인데 li를 클릭할때 이벤트에 걸린 함수가 작동해서 뭔지 궁금했다
위 현상과 관련된 것은 버블링이라는 것 때문
- https://ko.javascript.info/bubbling-and-capturing

```
event.target 이란?
event.target은 이벤트가 **실제로 발생한** 요소를 가리킨다.
단, IE에서는 event.target은 event.srcElement로 사용해야한다.
만약, parent 내부에 child 요소가 있고, child 요소에서 클릭 이벤트가 발생하면 event.target은 child이다.

event.currentTarget 이란?
event.currentTarget는 이벤트가 적용된 부모 요소 혹은 자신을 가리킨다.
단, IE에서는 currentTarget은 지원하지 않는다.

```
- https://mong-blog.tistory.com/entry/JS-eventtarget-eventcurrentTarget%EC%9D%98-%EC%B0%A8%EC%9D%B4feat-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%B2%84%EB%B8%94%EB%A7%81
