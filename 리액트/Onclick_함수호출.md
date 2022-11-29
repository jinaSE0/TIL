onClick이벤트와 연결된 컴포넌트에서 함수 호출할때 왜 함수()하면 안되는지 예전에 의문이었는데 상세하세 이유를 알게됨;;

onClick 이벤트는 말 그대로 사용자가 클릭이라는 행동을 하였을 때 발생하는 이벤트입니다. <br>
버튼이나 <a> tag 를 통한 링크 이동 등과 같이 주로 사용자의 행동에 따라 애플리케이션이 반응해야 할 때 자주 사용하는 이벤트입니다. 
그럼 위의 onChange 예시에 버튼을 추가하여 버튼 클릭 시 input tag 에 입력한 이름이 alert을 통해 알림 창이 팝업 되도록 코드를 추가해 보겠습니다.
```
function NameForm() {
  const [name, setName] = useState("");

  const handleChange = (e) => {
    setName(e.target.value);
  }

  return (
    <div>
      <input type="text" value={name} onChange={handleChange}></input>
      <button onClick={alert(name)}>Button</button>
      <h1>{name}</h1>
    </div>
  );
};
```
=> 위와 같이 onClick 이벤트에 alert(name) 함수를 바로 호출하면 컴포넌트가 렌더링 될 때 함수 자체가 아닌 함수 호출의 결과가 onClick 에 적용됩니다.<br>
때문에 버튼을 클릭할 때가 아닌, 컴포넌트가 렌더링 될 때에 alert 이 실행되고 <br>
따라서 그 결과인 undefined (함수는 리턴 값이 없을 때 undefined 를 반환합니다.) 가 onClick 에 적용되어 클릭했을 때 아무런 결과도 일어나지 않습니다. <br>
따라서 onClick 이벤트에 함수를 전달할 때는 함수를 호출하는 것이 아니라 아래와 같이 리턴문 안에서 함수를 정의하거나 <br>
리턴문 외부에서 함수를 정의 후 이벤트에 함수 자체를 전달해야 합니다.<br>

```
// 함수 정의하기

return (
  <div>
	...
    <button onClick={() => alert(name)}>Button</button>
	...
  </div>
  );
};

// 함수 자체를 전달하기

const handleClick = () => {
  alert(name);
};

return (
  <div>
      ...
    <button onClick={handleClick}>Button</button>
      ...
  </div>
  );
};
```
