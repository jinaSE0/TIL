<h2>innerHTML vs innerText vs textContent</h2>

```
html + css + javascript로 계산기를 구현하는 과정에서
innerHTML 과 textContent를 쓴 사람들이 있었는데
차이점을 알아보고자 한다.
일단 일반적인 text값을 가지고 올때는 세 가지 속성이 별 차이가 없으나
해당 요소가 가지고있는 컨텐츠의 내용에 따라서 차이가 난다.
```

- innerHTML <br>
  element의 속성
  해당 요소의 html, xml을 읽어오거나 설정<br>
  div안에 있는 HTML **전체** 내용을 가져옴 ('display:none' 숨겨진 부분까지 가져옴)


- innerText<br>
  element의 속성 <br>
  요소 내에서 사용자에게 **보여지는** 텍스트 값을 읽어옴<br>
  연속되는 공백은 무시하고, 숨겨진 텍스트는 보여주지않음

- textContent<br>
  node의 속성으로 <script>나 <style>태그와 상관없이<br>
  해당 노드가 가지고 있는 텍스트 값을 **그대로** 읽음
  
  
  
  출처 https://hianna.tistory.com/483
  
  계산기 구현쉽지않다.. 더 짧게 짧게 끊어서 생각하는 연습을 해야할 것같다.
  주말에 혼자서 온전히 만들어봐야지...
