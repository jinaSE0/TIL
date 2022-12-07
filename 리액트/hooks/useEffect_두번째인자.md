useEffect 두번째 인자
---
=> 뭘 넣는지에 따라 실행조건이 달라진다

```
function App() {
	const [keyword, setKeyword] = userState("");
	const onChange = (event) => seyKeyword(event.target.value);

	useEffect(() => {
		console.log("나는 업데이트가 될 때마다 작동해")
	}, ) //아무것도 안들어가 있을 때는 1. 컴포넌트가 처음 생성될때, 2. props가 업데이트 될때, 3. state가 업데이트 될때마다 실행됨

	useEffect(() => {
		console.log("나는 처음만 작동해")
	},[]) //빈 배열일때는 컴포넌트가 처음 생성될때만 함수가 실행됨

	useEffect(() => {
		console.log("나는 keyword가 바뀔 때마다 작동해")
	},[keyword])//키워드가 업데이트 될때마다 실행됨

	return (
		<div>
			<input
				value={keyword}
				onChange={onChange}
				type="text"
				placeholder="검색창..."
			/>
		</div>
	)
}
```
