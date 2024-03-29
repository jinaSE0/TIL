AJAX는 Asynchronous JavaScript And XMLHttpRequest의 약자
- JavaScript, DOM, Fetch, XMLHttpRequest, HTML 등의 다양한 기술을 사용하는 웹 개발 기법입니다.
- AJAX의 가장 큰 특징은, 웹 페이지에 필요한 부분에 필요한 데이터만 비동기적으로 받아와 화면에 그려낼 수 있다는 것입니다.
-  AJAX의 두 가지 핵심 기술
  -   JavaScript와 DOM, 그리고 Fetch
      ```
      전통적인 웹 애플리케이션에서는 <form> 태그를 이용해 서버에 데이터를 전송해야 했습니다.
      또한 서버는 요청에 대한 응답으로 새로운 웹 페이지를 제공해 주어야 했습니다.
      다시 말해, 클라이언트에서 요청을 보내면 매번 새로운 페이지로 이동해야 했습니다.
      그러나 Fetch를 사용하면, 페이지를 이동하지 않아도 서버로부터 필요한 데이터를 받아올 수 있습니다. 
      Fetch는 사용자가 현재 페이지에서 작업을 하는 동안 서버와 통신할 수 있도록 합니다. 
      즉, 브라우저는 Fetch가 서버에 요청을 보내고 응답을 받을 때까지 모든 동작을 멈추는 것이 아니라 계속해서 페이지를 사용할 수 있게 하는 비동기적인 방식을 사용합니다.
      또한 JavaScript에서 DOM을 사용해 조작할 수 있기 때문에, Fetch를 통해 전체 페이지가 아닌 필요한 데이터만 가져와 DOM에 적용시켜 새로운 페이지로 이동하지 않고
      기존 페이지에서 필요한 부분만 변경할 수 있습니다.
      ```
      
- AJAX의 장점
  ```
  - 서버에서 HTML을 완성하여 보내주지 않아도 웹페이지를 만들 수 있습니다.
  이전에는 서버에서 HTML을 완성하여 보내주어야 화면에 렌더링을 할 수 있었습니다. 
  그러나 AJAX를 사용하면 서버에서 완성된 HTML을 보내주지 않아도 필요한 데이터를 비동기적으로 가져와 브라우저에서 화면의 일부만 업데이트하여 렌더링 할 수 있습니다.

  - 표준화된 방법
  이전에는 브라우저마다 다른 방식으로 AJAX를 사용했으나, XHR이 표준화되면서부터 브라우저에 상관없이 AJAX를 사용할 수 있게 되었습니다.

  - 유저 중심 애플리케이션 개발
  AJAX를 사용하면 필요한 일부분만 렌더링하기 때문에 빠르고 더 많은 상호작용이 가능한 애플리케이션을 만들 수 있습니다.

  - 더 작은 대역폭
  대역폭: 네트워크 통신 한 번에 보낼 수 있는 데이터의 크기
  이전에는 서버로부터 완성된 HTML 파일을 받아와야 했기 때문에 한 번에 보내야 하는 데이터의 크기가 컸습니다. 
  그러나 AJAX에서는 필요한 데이터를 텍스트 형태(JSON, XML 등)로 보내면 되기 때문에 비교적 데이터의 크기가 작습니다.
  ```

4. AJAX의 단점
  ```
  - Search Engine Optimization(SEO)에 불리
  AJAX 방식의 웹 애플리케이션은 한 번 받은 HTML을 렌더링 한 후, 서버에서 비동기적으로 필요한 데이터를 가져와 그려냅니다. 
  따라서, 처음 받는 HTML 파일에는 데이터를 채우기 위한 틀만 작성되어 있는 경우가 많습니다. 
  검색 사이트에서는 전 세계 사이트를 돌아다니며 각 사이트의 모든 정보를 긁어와 사용자에게 검색 결과로 보여줍니다.
  AJAX 방식의 웹 애플리케이션의 HTML 파일은 뼈대만 있고 데이터는 없기 때문에 사이트의 정보를 긁어가기 어렵습니다.

  - 뒤로가기 버튼 문제
  일반적으로 사용자는 뒤로가기 버튼을 누르면 이전 상태로 돌아갈 거라고 생각하지만, 
  AJAX에서는 이전 상태를 기억하지 않기 때문에 사용자가 의도한 대로 동작하지 않습니다.
  따라서 뒤로가기 등의 기능을 구현하기 위해서는 별도로 History API를 사용해야 합니다.
  ```

