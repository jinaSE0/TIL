<h2>FATAL ERROR: Ineffective mark-compacts near heap limit Allocation failed</h2>

과제하는데 잘만 굴러가다가 이런 에러가 떴음...<br>
굉장히 단순한 과제를 하고 있었기때문에 서버가 터질리가 없는데 저런 메시지를 받은게 넘나 황당함..**<br>**
구글링하는데, 디버깅을 해서 문제를 찾아야하는데 아무리 생각해도 이 과제 수준에서 생길일이 절대 아닐거같아서 계속 서치서치함

계속 찾다보니 [이 블로그](https://velog.io/@nahyunbak/Next.js-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%88%84%EC%88%98-%ED%95%B4%EA%B2%B0-FATAL-ERROR-Ineffective-mark-compacts-near-heap-limit-Allocation-failed-JavaScript-heap-out-of-memory)에서
단서를 찾음

=> 아마도? 결론적으로 상호참조가 되어버려서 터진거라고 생각되어서 원인을 찾으러 나섬<br>
   위의 잠정적 결론을 바탕으로 뒤지다 보니 본인이 한 바보짓을 찾을 수 있었음...
```
일단 Footer 컴포넌트에 시멘틱 엘리먼트 요소로 푸터를 넣었는데 <footer>로 넣은 것이 아니라 
자동완성기능쓰다가 잘못선택해서 <Footer>로 컴포넌트 그 자체를 넣어서 터진 것...
```

잘하자, 좀?
  
  
