<h2>URL과 URI</h2>

URL
---
- Uniform Resource Locator의 줄임말로, 네트워크 상에서 웹 페이지, 이미지, 동영상 등의 파일이 위치한 정보를 나타냄

![image](https://user-images.githubusercontent.com/109025674/205205288-27d48f13-654b-484a-a9fe-5a0a9a399710.png)

- scheme,통신방식,프로토콜 / hosts 웹서버이름도메인ip사용해서 주소 / urlpath 웹서버에서 지정한 루트 디렉토리부터 시작해서 웹페이지 이미지 동영상등이 위치한 경로와 파일명

URI
---
- URI는 Uniform Resource Identifier 
- scheme, hosts, url-path +[ query, fragment]
=> 따라서 URI는 URL을 포함하는 상위개념

- query는 웹 서버에 보내는 추가적인 질문입니다. 
  위 그림의 http://www.google.com:80/search?q=JavaScript 를 브라우저의 검색창에 입력하면, 구글에서 JavaScript를 검색한 결과가 나타납니다.
- fragment는 일종의 북마크 기능을 수행하며 URL에 fragment(#)와 특정 HTML 요소의 id를 전달하면 해당 요소가 있는 곳으로 스크롤을 이동할 수 있습니다.

![dd](https://user-images.githubusercontent.com/109025674/205206516-69656981-69b4-4eac-9a76-da75faeaf697.PNG)
=> port는 서버로 진입할 수 있는 통로
