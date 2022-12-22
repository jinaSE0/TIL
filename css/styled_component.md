설치
---
```
# with npm
$ npm install --save styled-components

# with yarn
$ yarn add styled-components
```
```
//package.json에 다음 코드를 추가하면 여러 버전의 Styled Components가 설치되어 발생하는 문제가 줄어듦

{
  "resolutions": {
    "styled-components": "^5"
  }
}
```
```
import styled from "styled-components"
```

문법
---
1. 컴포넌트 만들기
```
import styled from "styled-components";

//Styled Components로 컴포넌트를 만들고
const 컴포넌트 이름 = styled.태그종류`
  css속성1 : 속성값;
  css속성2 : 속성값;
`;

export default function App() {
  // React 컴포넌트를 사용하듯이,,
  return <BlueButton>Blue Button</BlueButton>;
}

```

2. 컴포넌트 재활용해서 새 컴포넌트 만들기
```
import styled from "styled-components";

const BlueButton = styled.button`
  background-color: blue;
  color: white;
`;

//재활용
const BigBlueButton = styled(BlueButton)` //()안에 재활용할 컴포넌트를 써주면 됨
  padding: 10px; // 추가하고싶은 스타일 속성을 넣어줌
  margin-top: 10px;
`;

//재활용한 컴포넌트를 재활용할 수도 있음.
const BigRedButton = styled(BigBlueButton)`
  background-color: red;
`;

export default function App() {
  return (
    <>
      <BlueButton>Blue Button</BlueButton>
      <br />
      <BigBlueButton>Big Blue Button</BigBlueButton>
      <br />
      <BigRedButton>Big Red Button</BigRedButton>
    </>
  );
}
```
3. props 활용하기
=> React 컴포넌트처럼 props를 내려줄 수 있고, 내려준 props 값에 따라서 컴포넌트를 렌더링하는 것도 가능

```
const 컴포넌트이름 = styled.태그종류`
  background: ${(props) => 함수종류};
`;
//Styled Components는 템플릿 리터럴 문법( ${ } )을 사용하여 JavaScript 코드를 사용
//props를 받아오려면 props를 인자로 받는 함수를 만들어 사용
```
- props로 조건부 렌더링

```
mport styled from "styled-components";
import GlobalStyle from "./GlobalStyle";

const Button1 = styled.button`
  background: ${(props) => (props.skyblue ? "skyblue" : "white")};
`;

export default function App() {
  return (
    <>
      <GlobalStyle />
      <Button1>Button1</Button1> //하얀 버튼이 나오고
      <Button1 skyblue>Button1</Button1> //파란 버튼이 나옴
    </>
  );
}

```
- props값으로 렌더링 하기

```
import styled from "styled-components";
import GlobalStyle from "./GlobalStyle";

//받아온 prop 값을 그대로 이용해 렌더링
const Button1 = styled.button`
  background: ${(props) => (props.color ? props.color : "white")};
`;
//또는 이렇게도 가능
const Button2 = styled.button`
  background: ${(props) => props.color || "white"};
`;

export default function App() {
  return (
    <>
      <GlobalStyle />
      <Button1>Button1</Button1> //이것만 하얀 버튼
      <Button1 color="orange">Button1</Button1>
      <Button1 color="tomato">Button1</Button1>
      <br />
      <Button2>Button2</Button2> //이것만 하얀 버튼
      <Button2 color="pink">Button2</Button2>
      <Button2 color="turquoise">Button2</Button2>
    </>
  );
}
```


4. 전역 스타일 설정하기
- Styled Components에서 createGlobalStyle 함수를 불러옵니다.
```
import { createGlobalStyle } from "styled-components";
```
- 그 다음 이 함수를 사용해 CSS 파일에서 작성하듯 설정해주고 싶은 스타일을 작성합니다.

```
const GlobalStyle = createGlobalStyle`
	button {
		padding : 5px;
    margin : 2px;
    border-radius : 5px;
	}
`
```
- 이렇게 만들어진 <GlobalStyle> 컴포넌트를 최상위 컴포넌트에서 사용해주면 전역에 <GlobalStyle> 컴포넌트의 스타일이 적용됩니다.
```
function App() {
	return (
		<>
			<GlobalStyle />
			<Button>전역 스타일 적용하기</Button>
		</>
	);
}
```
