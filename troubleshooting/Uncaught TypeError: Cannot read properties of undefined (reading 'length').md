```
장바구니 추가 기능을 구현하는데 분명 맞게 했다고 생각하는데 안되고 콘솔창에 계속 아래와 같은 메시지가 뜸
Uncaught TypeError: Cannot read properties of undefined (reading 'length')
그래서 length를 오타낸 줄 알고 (오타 실수 아주 잘 함..) 몇 번이고 봐도 맞다...
구글링해보니 [이런 블로그 글](https://junibong.tistory.com/72)을 보게 되었고
변수에 데이터가 없을 경우 이런 상황이 발생한다고 해서
콘솔로 제대로 데이터가 불러와지는지 체크해보니 undefined라 뜬다.
그래서 프롭스를 내려주는걸 타고 타고 올라가니 App.js에 setItems 함수만 잘넘겨주고 Items는 안넘김ㅋㅋㅋㅋㅋㅋㅋ
처음부터 어떤 프롭스 내려줄지 꼼꼼히 그림을 그려서 잘 내려 주자....
```
App.js
```
import React, { useState } from "react";
import Nav from "./components/Nav";
import ItemListContainer from "./pages/ItemListContainer";
import "./App.css";
import "./variables.css";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import ShoppingCart from "./pages/ShoppingCart";
import { initialState } from "./assets/state";

function App() {
  const [items, setItems] = useState(initialState.items);
  const [cartItems, setCartItems] = useState(initialState.cartItems);

  return (
    <Router>
      <Nav cartItems={cartItems} />
      <Routes>
        <Route
          path="/"
          element={
            <ItemListContainer
              items={items}
              cartItems={cartItems}
              setCartItems={setCartItems}
            />
          }
        />
        <Route
          path="/shoppingcart"
          element={
            <ShoppingCart
              cartItems={cartItems}
              items={items}
              setCartItems={setCartItems}
            />
          }
        />
      </Routes>
      <img
        id="logo_foot"
        src={`${process.env.PUBLIC_URL}/codestates-logo.png`}
        alt="logo_foot"
      />
    </Router>
  );
}

export default App;

```
itemListContainer.js
```
import React from "react";
import CartItem from "../components/CartItem";
import Item from "../components/Item";

function ItemListContainer({ items, cartItems, setCartItems }) {
  const handleClick = (e, id) => {
    console.log(cartItems);
    let newCartItem = {};
    newCartItem.itemId = id;
    newCartItem.quantity = 1;
    for (let i = 0; i < cartItems.length; i++) {
      if (cartItems[i].itemId !== id) {
        setCartItems([...cartItems, newCartItem]);
      } else {
        setCartItems([...cartItems]);
        cartItems[i].quantity++;
      }
    }
  };
  return (
    <div id="item-list-container">
      <div id="item-list-body">
        <div id="item-list-title">쓸모없는 선물 모음</div>
        {items.map((item, idx) => (
          <Item item={item} key={idx} handleClick={handleClick} />
        ))}
      </div>
    </div>
  );
}

export default ItemListContainer;


```
