HTTP Responses
- Status line <br>
  HTTP Responses는 서버가 클라이언트에게 보내는 메시지입니다. 응답의 첫 줄을 Status line이라고 부르며, 다음의 정보를 포함합니다.

  - 현재 프로토콜의 버전(HTTP/1.1)
  - 상태 코드 - 요청의 결과를 나타냅니다. (ex. 200, 302, 404 등)
  - 상태 텍스트 - 상태 코드에 대한 설명
  - Status line의 한 예시로 HTTP/1.1 404 Not Found가 있습니다.

- Headers
응답에 들어가는 HTTP headers는 요청 헤더와 동일한 구조를 가지고 있습니다. 대소문자 구분 없는 문자열, 콜론(:), 값을 입력합니다. 값은 헤더에 따라 다릅니다. 요청의 헤더와 마찬가지로 몇 그룹으로 나눌 수 있습니다.

  - General headers : 메시지 전체에 적용되는 헤더로, body를 통해 전송되는 데이터와는 관련이 없는 헤더입니다.
  - Response headers : 위치 또는 서버 자체에 대한 정보(이름, 버전 등)와 같이 응답에 대한 부가적인 정보를 갖는 헤더로, Vary, Accept-Ranges와 같이 상태 줄에 넣기에는 공간이 부족했던 추가 정보를 제공합니다.
  - Representation headers : 이전에는 Entity headers로 불렀으며, body에 담긴 리소스의 정보(콘텐츠 길이, MIME 타입 등)를 포함하는 헤더입니다.

![image](https://user-images.githubusercontent.com/109025674/205429163-94181db1-2b54-4041-a434-c7d9d748886c.png)


- Body
응답의 본문은 HTTP messages 구조의 마지막에 위치합니다. 모든 응답에 body가 필요하지는 않습니다. 201, 204와 같은 상태 코드를 가지는 응답에는 본문이 필요하지 않습니다. 응답의 body는 다음과 같이 두 종류로 나눌 수 있습니다.
  - Single-resource bodies(단일-리소스 본문) :
    - 길이가 알려진 단일-리소스 본문은 두 개의 헤더(Content-Type, Content-Length)로 정의합니다.
    - 길이를 모르는 단일 파일로 구성된 단일-리소스 본문은 Transfer-Encoding이 chunked 로 설정되어 있으며, 파일은 chunk로 나뉘어 인코딩되어 있습니다.
  - Multiple-resource bodies(다중-리소스 본문) : 서로 다른 정보를 담고 있는 body입니다.
