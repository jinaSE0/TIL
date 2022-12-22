useRef
---

아래와 같이 예외적으로 리액트에서 DOM 노드, 엘리먼트, 그리고 React 컴포넌트 주소값을 참조할 필요가 있음 => useRef 사용
- focus
- text selection
- media playback
- 애니메이션 적용
- d3.js, greensock 등 DOM 기반 라이브러리 활용

```
const 주소값을_담는_그릇 = useRef(참조자료형)
// 이제 주소값을_담는_그릇 변수에 어떤 주소값이든 담을 수 있습니다.
return (
    <div>
      <input ref={주소값을_담는_그릇} type="text" />
        {/* React에서 사용 가능한 ref라는 속성에 주소값을_담는_그릇을 값으로 할당하면*/}
        {/* 주소값을_담는_그릇 변수에는 input DOM 엘리먼트의 주소가 담깁니다. */}
        {/* 향후 다른 컴포넌트에서 input DOM 엘리먼트를 활용할 수 있습니다. */}
    </div>);
```
이 주소값은 컴포넌트가 re-render 되더라도 바뀌지 않아서 아래와 같이 제한된 상황에서 useRef 를 활용할 수 있음
```
function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  const onButtonClick = () => {
    inputEl.current.focus();
  };
  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>);
}
```
예시1
```
import React, { useRef } from "react";

const Focus = () => {
  const firstRef = useRef(null);
  const secondRef = useRef(null);
  const thirdRef = useRef(null);

  const handleInput = (event) => {
    console.log(event.key, event);
    if (event.key === "Enter") {
      if (event.target === firstRef.current) {
        secondRef.current.focus();
        event.target.value = "";
      } else if (event.target === secondRef.current) {
        thirdRef.current.focus();
        event.target.value = "";
      } else if (event.target === thirdRef.current) {
        firstRef.current.focus();
        event.target.value = "";
      } else {
        return;
      }
    }
  };

  return (
    <div>
      <h1>타자연습</h1>
      <h3>각 단어를 바르게 입력하고 엔터를 누르세요.</h3>
      <div>
        <label>hello </label>
        <input ref={firstRef} onKeyUp={handleInput} />
      </div>
      <div>
        <label>world </label>
        <input ref={secondRef} onKeyUp={handleInput} />
      </div>
      <div>
        <label>codestates </label>
        <input ref={thirdRef} onKeyUp={handleInput} />
      </div>
    </div>
  );
};

export default Focus;
```
예시2
```
import { useRef } from "react";

export default function App() {
  const videoRef = useRef(null);

  const playVideo = () => {
    videoRef.current.play();
    console.log(videoRef.current);
  };

  const pauseVideo = () => {
    videoRef.current.pause();
    videoRef.current.remove();
  };

  return (
    <div className="App">
      <div>
        <button onClick={playVideo}>Play</button>
        <button onClick={pauseVideo}>Pause</button>
      </div>
      <video ref={videoRef} width="320" height="240" controls>
        <source
          type="video/mp4"
          src="https://player.vimeo.com/external/544643152.sd.mp4?s=7dbf132a4774254dde51f4f9baabbd92f6941282&profile_id=165"
        />
      </video>
    </div>
  );
}

```
