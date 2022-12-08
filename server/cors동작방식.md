CORS 동작 방식
CORS의 동작 방식에는 크게 세 가지가 있습니다.

1. 프리플라이트 요청 (Preflight Request)
실제 요청을 보내기 전, OPTIONS 메서드로 사전 요청을 보내 해당 출처 리소스에 접근 권한이 있는지부터 확인하는 것을 프리플라이트 요청이라고 합니다.

![image](https://user-images.githubusercontent.com/109025674/206337830-6283245f-f9d6-4148-91d2-117fc45f314e.png)
위 이미지의 흐름과 같이, 브라우저는 서버에 실제 요청을 보내기 전에 프리플라이트 요청을 보내고, 응답 헤더의 Access-Control-Allow-Origin으로 요청을 보낸 출처가 돌아오면 실제 요청을 보내게 됩니다.
![image](https://user-images.githubusercontent.com/109025674/206337882-819c0eb9-ea8f-4057-ab69-187892eaf7b3.png)
만약에 요청을 보낸 출처가 접근 권한이 없다면 브라우저에서 CORS 에러를 띄우게 되고, 실제 요청은 전달되지 않습니다.

프리플라이트 요청은 왜 필요한 걸까요?

실제 요청을 보내기 전에 미리 권한 확인을 할 수 있기 때문에, 실제 요청을 처음부터 통째로 보내는 것보다 리소스 측면에서 효율적입니다.
CORS에 대비가 되어있지 않은 서버를 보호할 수 있습니다. CORS 이전에 만들어진 서버들은 SOP 요청만 들어오는 상황을 고려하고 만들어졌습니다. 따라서 다른 출처에서 들어오는 요청에 대한 대비가 되어있지 않았습니다.

![image](https://user-images.githubusercontent.com/109025674/206337948-84b6af38-f68e-45f3-a5aa-5d8350cc3f92.png)이런 서버에 바로 요청을 보내면, 응답을 보내기 전에 우선 요청을 처리하게 됩니다. 브라우저는 응답을 받은 후에야 CORS 권한이 없다는 것을 인지하지만, 브라우저가 에러를 띄운 후에는 이미 요청이 수행된 상태가 됩니다. 만약에 들어온 요청이 DELETE 나 PUT 처럼 서버의 정보를 삭제하거나 수정하는 요청이었다면? 생각만 해도 아찔합니다.

하지만 CORS에 대비가 되어있지 않은 서버라도 프리플라이트 요청을 먼저 보내게 되면, 프리플라이트 요청에서 CORS 에러를 띄우게 됩니다. 예시와 같이 실행되선 안 되는 Cross-Origin 요청이 실행되는 것을 방지할 수 있는 것이죠. 이런 이유로 프리플라이트 요청이 CORS의 기본 사양으로 들어가게 되었습니다.
2. 단순 요청 (Simple Request)
단순 요청은 특정 조건이 만족되면 프리플라이트 요청을 생략하고 요청을 보내는 것을 말합니다.
![image](https://user-images.githubusercontent.com/109025674/206337979-cfaf842b-cb99-4203-81bc-58aa37ee4474.png)
조건은 다음과 같습니다. 하지만 이 조건들을 모두 만족시키기는 어려우므로, 일단은 참고만 해주세요.

GET, HEAD, POST 요청 중 하나여야 합니다.
자동으로 설정되는 헤더 외에, Accept, Accept-Language, Content-Language, Content-Type 헤더의 값만 수동으로 설정할 수 있습니다.
Content-Type 헤더에는 application/x-www-form-urlencoded, multipart/form-data, text/plain 값만 허용됩니다.
3. 인증정보를 포함한 요청 (Credentialed Request)
요청 헤더에 인증 정보를 담아 보내는 요청입니다. 출처가 다를 경우에는 별도의 설정을 하지 않으면 쿠키를 보낼 수 없습니다. 민감한 정보이기 때문입니다. 이 경우에는 프론트, 서버 양측 모두 CORS 설정이 필요합니다.

프론트 측에서는 요청 헤더에 withCredentials : true 를 넣어줘야 합니다.
서버 측에서는 응답 헤더에 Access-Control-Allow-Credentials : true 를 넣어줘야 합니다.
서버 측에서 Access-Control-Allow-Origin 을 설정할 때, 모든 출처를 허용한다는 뜻의 와일드카드(*)로 설정하면 에러가 발생합니다. 인증 정보를 다루는 만큼 출처를 정확하게 설정해주어야 합니다.
