# 리액트에 대한 이해

### Javascript로 구현했을 때의 특징

- 상태에 따른 UI를 바꾸기 위해서 DOM 노드를 직접 조작해야 한다.
  - DOM 노드를 직접 조작하는 예시
  - `content.innerHTML = dataMap[key]`

### React로 구현했을 때의 특징

- UI 로직과 비즈니스 로직(데이터 - 상태값)을 분리 할 수 있다
  - 쉽게 말해서 이전 뷰를 날린 다음 결과적으로 보여줘야 하는 뷰를 다시 보여줍니다.
- 리액트는 내부적으로 Virtual DOM 이라는 것을 통해 변경된 부분만 업데이트 할 수 있게 합니다.
- 예시
  - Js에서 쓰였던 `content.innerHTML = dataMap[key]` 처럼 DOM을 직접 조작하는 부분이 없습니다.

```
import { useState } from "react";
import "./styles.css";

export default function App() {
  const [key, setKey] = useState("메일");
  const dataMap = {
    메일: "메일함을 확인하세요.",
    카페: "즐겨찾는 카페의 새 소식을 확인해보세요.",
    블로그: "오늘을 기록해보세요."
  };

  function clickTabItem(e) {
    setKey(e.target.id);
  }

  return (
    <div className="App">
      <div className="container">
        <div className="tab-items">
          <div className="tab-item" id="메일" onClick={clickTabItem}>
            메일
          </div>
          <div className="tab-item" id="카페" onClick={clickTabItem}>
            카페
          </div>
          <div className="tab-item" id="블로그" onClick={clickTabItem}>
            블로그
          </div>
        </div>
        <div className="tab-content-wrapper">{dataMap[key]}</div>
      </div>
    </div>
  );
}
```

### Babel

- Babel은 자바스크립트 컴파일러다. 입력은 자바스크립트 코드고 출력도 자바스크립트 코드다. 최신 버전의 자바스크립트 문법은 브라우저가 이해하지 못하기 때문에 babel이 브라우저가 이해할 수 있는 문법으로 변환해준다. ES6, ES7 등의 최신 문법을 사용해서 코딩을 할 수 있기 때문에 생산성이 향상된다.
- babel.config.js
  - `npx babel src/indexedDB.js --presets=@babel/preset-react`
  - 이와 같이 babel을 사용할 때 매번 이렇게 확인하면 번거롭기 때문에
  - babel.config.js 를 통해 설정을 해줍니다.
  - [참고링크](https://babeljs.io/docs/en/configuration)

### Webpack

- 바벨이 컴파일러라면 웹팩은 번들러이다.
  - 번들러 : 번들러(Bundler)는 분리된 JavaScript와 CSS 모듈 코드를 브라우저에 최적화된 여러 개의 파일로 결합합니다. React 애플리케이션에서 널리 사용되는 번들러에는 Webpack과 Browserify가 있습니다.

### HMR(Hot Module Replacement)

- Hot Module Replacement(또는 HMR)는 webpack에서 제공하는 가장 유용한 기능 중 하나입니다. 모든 종류의 모듈을 새로고침 할 필요 없이 런타임에 업데이트 할 수 있습니다.
- [참고링크](https://webpack.kr/guides/hot-module-replacement)
