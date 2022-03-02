## 화살표 함수

화살표 함수의 경우 괄호()로 감싸진 부분이 return 된다(return문을 작성하지 않아도 return 됨).

반면에 중괄호{}로 감싸진 다음과 같은 함수는 return문이 없다면 return 값을 반환하지 않는다.

---

45. deploying our app gh-pages를 통해 github 블로그에 프로젝트 업로드하기

먼저 deploy하려는 폴더로 옮겨준다
ex. cd monster-rolodex

외부장소 깃허브 주소를 등록한다
git remote add origin 원격주소

이후 yarn add gh-pages 설치

이후 package.json 들어간다

"homepage": "https://chaesono.github.io/monsters-rolodex" 추가

"script" 안에
"predeploy": "yarn build",
"deploy": "gh-pages -d build"
추가
스크립트 부분에 deploy와 predeploy를 설정해준다.

npm은 deploy를 실행하기 전 predeploy를 자동으로 먼저 실행한다.

build를 진행하고, 이를 통해 생성된 build폴더를 이용해 deploy를 진행한다.

이후 yarn deploy

이후 git add -A

이후 커밋 git commit -m "message"

이후 git push origin master

---

jsx 정리

라이프사이클 정리

node 개발자는 변수 하나만 export 하는 등의 방식이 빈번히 사용되는데, front end 개발자의 경우는 constructor나 class를 export 하는 경우가 많다. 이런 경우 하나의 module이 하나의 export만 갖는 경우가 되는데 이런 때 사용할 수 있는 것이 default exports 이다.

sass란

CSS를 효율적으로 작성할 수 있도록 도와주는 프로그램이다.

기존의 CSS의 유지보수의 불편함 등을 SASS를 사용하면 해결 할 수 있다.

위에서 언급한 CSS의 단점을 보완하기 위한 기술로, SASS 자체를 그대로 사용할수는 없고, SASS의 문법에 맞게 SASS파일을 만들면 컨버터를 이용해서 CSS를 생성한다.

즉, SASS문법에 맞게 CSS를 작성하고, SASS 컴파일러를 사용하여 HTML이 이해 할 수 있는 문법으로 변환합니다.

```sh
yarn add node-sass
```

react 에서 inline style css 방식

```js
<div
  style={{
    display: "inline-block",
    width: "100px",
    height: "100px",
  }}
></div>
```

https://velog.io/@sdc337dc/0.%ED%81%B4%EB%9E%98%EC%8A%A4%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8 참고

## react-router-dom

yarn add react-router-dom

리액트 라우터에서 제공하는 몇 가지 기본 컴포넌트의 역할은 다음과 같다.

<BrowserRouter />: HTML5 히스토리 API를 사용하여 주소를 관리하는 라우터(해쉬뱅 모드 사용 안함)
<Route />: 요청 경로와 렌더링할 컴포넌트를 설정한다
<Switch />: 하위에 라우터 중 하나를 선택한다
<Redirect />: 요청 경로를 다른 경로로 리다이렉션한다

<Link to='/topics'>Topics</Link>

props를 출력시 history, location, match 가 나옵니다.

1. match

- path, url, isExact, params
  - url : 주소에 입력하는 내용이 저장됩니다.
  - path : vs code에서 설정한 path
  - isExact : url의 패턴이 완벽히 일치할 때 true를 반환합니다.
  - params : /:id 부분에 해당합니다.

2. history

- Link를 쓰지않고 동적으로 활용하려면 onclick메소드에 props.history.push('/topics')를 설정하면 됩니다.

3. location

- pathname
  - 주소에 입력하는 내용이 저장됩니다.

HOC withRouter // history.push를 쓰기위해 export default withRouter(connect(mapStateToProps)(CartDropdown)); 이런식으로 연결해줍니다.

## firebase

1. yarn add firebase
2. firebase.utils.js 생성 후
3. import firebase from 'firebase/app'

shapShot 공부하기

## Redux

https://medium.com/@jsh901220/react%EC%97%90-redux-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0-a8e6efd745c9 참고

yarn add redux redux-logger react-redux 설치 후
index.js 에

```jsx
import { Provider } from "react-redux";

import "./index.css";
import App from "./App";

ReactDOM.render(
  <Provider>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </Provider>,
  document.getElementById("root")
);
```

이런식으로 추가합니다.

```jsx
const mapStateToProps = ({ cart: { cartItems } }) => ({
  itemCount: cartItems.reduce(
    (accumalatedQuantity, cartItem) => accumalatedQuantity + cartItem.quantity,
    0
  ),
});

// 이런식으로 코드를 짜면 매번 새로 rerender 하기때문에 좋지않습니다.
// yarn add reselect 설치후

// cart.selector 생성 후
import { createSelector } from "reselect";

const selectCart = (state) => state.cart;

export const selectCartItems = createSelector(
  [selectCart],
  (cart) => cart.cartItems
);

export const selectCartItemsCount = createSelector(
  [selectCartItems],
  (cartItems) =>
    cartItems.reduce(
      (accumalatedQuantity, cartItem) =>
        accumalatedQuantity + cartItem.quantity,
      0
    )
);

const mapStateToProps = (state) => ({
  itemCount: selectCartItemsCount(state),
});
// 이렇게 바꿔줍니다.
```

reselect 정리

mapStateToProps 로 connect를 했으면 mapDispatchToProps를 2번째인자로 굳이 또 설정할 필요가 없다 dispatch 함수는 알아서 써진다?

---

yarn add redux-persist

- data-normalization

```jsx
export const selectCollection = (collectionUrlParam) =>
  createSelector([selectCollections], (collections) =>
    collections.find(
      (collection) => collection.id === COLLECTION_ID_MAP[collectionUrlParam]
    )
  );
```

이런식으로 코드를짜면 콜렉션이 많을때 find를 하면 좋지않은 코드입니다.

배열로 저장했던것을 object로 바꿔줍니다.

```jsx
export const selectCollection = (collectionUrlParam) =>
  createSelector(
    [selectCollections],
    (collections) => collections[collectionUrlParam]
  );
```

이렇게 바꿔줍니다.

## 결제시스템 만들기

1. yarn add react-stripe-checkout

StripeCheckout에 관한 인자는 https://github.com/azmenak/react-stripe-checkout 참고

heroku create crwn-live --buildpack https://github.com/chaesono/create-react-app-buildpack.git // 리액트관련해서 생성할때 가장 효율

## development

```jsx
if (process.env.NODE_ENV === "development") {
  middlewares.push(logger);
}
// 개발할때만 logger를 표시합니다.
```

## styled-components 사용이유

https://analogcoding.tistory.com/181

## QueryReference and QuerySnapshot

documentRef vs collectinoRef

```js
const userRef = firestore.doc(`users/${userAuth.uid}`); //documentRef
const collectionRef = firestore.collection("users"); // CollectionRef

const snapShot = await userRef.get();
const collectionSnapshot = await collectionRef.get();
console.log({ collection: collectionSnapshot.docs.map((doc) => doc.data()) });
console.log(snapShot.data());
```

## Higer Order Component 정리
