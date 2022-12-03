HTTP Requests
- Start line : HTTP Requests는 클라이언트가 서버에게 보내는 메시지입니다. 

  => Start line의 세가지 요소
  1. 수행할 작업(GET, PUT, POST 등)이나 방식(HEAD or OPTIONS)을 설명하는 HTTP method를 나타냅니다.<br>
     예를 들어 GET method는 리소스를 받아야 하고, POST method는 데이터를 서버로 전송합니다.
  2. 요청 대상(일반적으로 URL이나 URI) 또는 프로토콜, 포트, 도메인의 절대 경로는 요청 컨텍스트에 작성됩니다. 이 요청 형식은 HTTP method 마다 다릅니다.
    - origin 형식 : '?'와 쿼리 문자열이 붙는 절대 경로입니다. GET, POST, HEAD, OPTIONS 등의 method와 함께 사용합니다.
      - POST / HTTP 1.1
      - GET /background.png HTTP/1.0
      - HEAD /test.html?query=alibaba HTTP/1.1
      - OPTIONS /anypage.html HTTP/1.0
    - absolute 형식 : 완전한 URL 형식으로, 프록시에 연결하는 경우 대부분 GET method와 함께 사용합니다.
      - GET http://developer.mozilla.org/en-US/docs/Web/HTTP/Messages HTTP/1.1
    - authority 형식 : 도메인 이름과 포트 번호로 이루어진 URL의 일부분 입니다. HTTP 터널을 구축하는 경우, CONNECT와 함께 사용할 수 있습니다.
      - CONNECT developer.mozilla.org:80 HTTP/1.1
    - asterisk 형식 : OPTIONS 와 함께 별표(*) 하나로 서버 전체를 표현합니다.
      - OPTIONS * HTTP/1.1
  
HTTP 버전에 따라 HTTP message의 구조가 달라집니다. 따라서 start line에 HTTP 버전을 함께 입력합니다.

- Headers
요청의 Headers는 기본 구조를 따릅니다. 헤더 이름(대소문자 구분이 없는 문자열), 콜론( : ), 값을 입력합니다. 값은 헤더에 따라 다릅니다. 여러 종류의 헤더가 있고, 다음과 같이 그룹을 나눌 수 있습니다.

General headers : 메시지 전체에 적용되는 헤더로, body를 통해 전송되는 데이터와는 관련이 없는 헤더입니다.
Request headers : fetch를 통해 가져올 리소스나 클라이언트 자체에 대한 자세한 정보를 포함하는 헤더를 의미합니다. User-Agent, Accept-Type, Accept-Language와 같은 헤더는 요청을 보다 구체화합니다. Referer처럼 컨텍스트를 제공하거나 If-None과 같이 조건에 따라 제약을 추가할 수 있습니다.
Representation headers : 이전에는 Entity headers로 불렀으며, body에 담긴 리소스의 정보(콘텐츠 길이, MIME 타입 등)를 포함하는 헤더입니다.

![image](https://user-images.githubusercontent.com/109025674/205428647-ff1fb855-35d8-4719-ab30-b3c178f6a166.png)

- Body
요청의 본문은 HTTP messages 구조의 마지막에 위치합니다. 모든 요청에 body가 필요하지는 않습니다. GET, HEAD, DELETE, OPTIONS처럼 서버에 리소스를 요청하는 경우에는 본문이 필요하지 않습니다. 
POST나 PUT과 같은 일부 요청은 데이터를 업데이트하기 위해 사용합니다. body는 다음과 같이 두 종류로 나눌 수 있습니다.
  - Single-resource bodies(단일-리소스 본문) : 헤더 두 개(Content-Type과 Content-Length)로 정의된 단일 파일로 구성됩니다.
  - Multiple-resource bodies(다중-리소스 본문) : 여러 파트로 구성된 본문에서는 각 파트마다 다른 정보를 지닙니다. 보통 HTML form과 관련이 있습니다.
