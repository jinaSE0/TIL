Express 서버가 HTTP 요청을 받게되면, res를 반환하게 되는데,
반환하는 법으로는 res.json()_res.send()_res.end()가 있음

```
res.send()는 send에 전해진 인자의 타입에 따라서 Content-type이 자동적으로 만들어진다. 

res.json()은 json이 아닌 것도 json 형식으로 바꾸어서 보내준다. 
즉 content-type 헤더를 application/JSON으로 고정한다. 그런데 결국 res.json()도 마지막에 res.send()를 호출한다.

res.end()는 보내줄 아무 데이터도 없는데 response를 끝내고 싶을 때 사용한다.
-> 굳이 쓸 필요는 없다
ex) res.status(400).end();
```
