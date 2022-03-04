# 1. HTML/CSS 기본

[구조] HTML : 웹 문서의 기본적인 골격을 담당
[표현] CSS : 각 요소들의 레이아웃, 스타일링을 담당
[동작] JavaScript : 동적인 요소(사용자와의 인터렉션)을 담당

- 웹 표준

  - HTML5는 W3C에서 2014년에 공식 표준화
  - 2019년에 WHATWG(애플, 모질라, 구글, MS)에 의해 HTML Living Standard(HTML5의 개선안)가 표준화됨
  - HTML이 표준화 되기 이전에는, 익스플로러의 액티브X처럼 독자적인 플러그인이 존재하기도 하였음
  - 웹 표준을 준수하여 작성한다면 운영체제, 브라우저마다 의도된 대로 보여지는 웹 페이지를 만들 수 있음

- 웹 접근성

  - 웹 접근성은 장애를 가진 사람과 장애를 가지지 않은 사람 모두가 웹사이트를 이용할 수 있게 하는 방식을 가리킨다.
    - 팔이 부러지거나 안경을 잃어버려서 일시적인 장애를 겪는 사람
    - 느린 인터넷을 사용하거나 제한적이거나 비싼 대역폭을 사용하는 사람
  - 웹 브라우징에 쓰이는 보조과학기술 : 스크린리더, 화면 돋보기, 음성 인식, 키보드 오버레이 등

- 웹 호환성 (Cross Browsing)

  - 웹 브라우저 버전, 종류와 관계없는 웹사이트 접근
  - 웹 표준 준수를 통한 브라우저 호환성 확보

- 블록과 인라인

  - 블록
    - 블록 레벨 요소는 언제나 새로운 줄에서 시작하고, 좌우 양쪽으로 최대한 늘어나 가능한 모든 너비를 차지합ㄴ디ㅏ.
    - 상자를 아래로 쌓는 것!
  - 인라인

    - 인라인 요소는 줄의 어느 곳에서나 시작할 수 있습니다.
    - 바로 이전 요소가 끝나는 지점부터 시작하여, 요소의 내용(content)만큼만 차지합니다.

- 콘텐츠 카테고리
  - HTML5 부터 비슷한 특징을 가진 요소끼리 묶어서 7가지 카테고리로 세분화
  - 하나의 HTML 요소가 여러 콘텐츠 카테고리 내의 포함관계에 들어갈 수도 있다.
  1. 메타데이터 콘텐츠(Metadata Content)
     - 문서의 메타 데이터(정보), 다른 문서를 가리키는 링크 등을 나타내는 요소
  2. 플로우 콘텐츠(Flow Content)
     - 웹 페이지상에 메타데이터를 제외하고 거의 모든 요소, 보통 텍스트나 임베디드 콘텐츠를 포함
  3. 섹션 콘텐츠(Section Content)
     - 웹 문서의 구획(Section)을 나눌 때 사용
  4. 헤딩 콘텐츠(Heading Content)
     - 섹션의 제목(heading)과 관련된 요소
  5. 프레이징 콘텐츠(Phrasing Content)
     - 문단에서 텍스트를 마크업 할 때 사용
  6. 임베디드 콘텐츠(Embedded Content)
     - 이미지나 비디오 등 외부 소스를 가져오거나 삽입할 때 사용되는 요소
  7. 인터렉티브 콘텐츠(Interactive Content)
     - 사용자와의 상호작용을 위한 컨텐츠 요소

# 텍스트 요소

- blockquote, q : 인용문

```html
<blockquote>cite="https://www.naver.com"</blockquote>
<q></q>
```

cite는 출처

- pre : 미리 서식을 지정한 텍스트를 나타낸다.
- figure : figure 요소는 독립적인 콘텐츠를 표현합니다.
- ficaption : figure에 대한 설명문(사진에대한 설명)
- hr : 수평선
- b, strong : 둘다 강조이지만 스크린리더기에서 strong은 더 강조해서 읽는다.
- em : 기울임 strong은 위험한 중요한것에 강조이지만 em은 단순히 그냥 조금 더 강조하는 곳에 쓰임 em 역시 스크린리더기에서 강조하며 읽음
- i : 기울임, 스크린 리더기가 강조하진 않지만, 기술 용어, 외국어 구절, 등장인물의 생각 등 분위기가 바뀔때 쓰는 기울임

# 시멘틱 웹

- header, nav, main, article, footer : div와 같음 하지만 의미가 있기에 Semantic tag라 부름
- div(블록 요소), span(인라인 요소) : non-semantic tag

## 장점

- 검색 엔진은 의미론적 마크업을 분석하여 페이지의 검색 랭킹에 영향을 줄 수 있는 중요한 키워드로 간주합니다.
- 시각 장애가 있는 사용자가 스크린리더로 페이지를 탐색할 때 의미론적 마크업을 푯말로 사용할 수 없습니다.
- 의미가 없는 끊임없는 `div` 들을 탐색하는 것보다, 의미있는 코드 블록을 찾는 것이 훨씬 쉽습니다.
- 개발자에게 태그 안에 채워질 데이터 유형을 제안합니다.
- 의미있는 이름짓기(Semanting naming)는 적절한 사용자 정의 요소 / 구성 요소의 이름짓기를 반영합니다.

# 폼 Form

```html
<div>
  <label for="foodname">음식 이름 : </label>
  <input type="text" name="food" id="foodname" />
</div>

<div>
  <label>
    색깔 :
    <input type="text" name="color" />
  </label>
</div>
```

- input의 `autocomplete="on"` 속성은 자동완성 기능이 켜집니다.
- input의 `required` 속성은 무조건 작성해야 할 때 부여하는 속성입니다.
- button은 input보다 스타일을 적용하기 수월하다.

- label의 자식요소로 input을 쓰게되면 따로 id를 부여하지 않아도 된다.

```html
<form action="" method="GET">
  <label for="movie">좋아하는 영화 : </label>
  <select name="movie" id="movie" required>
    <option value="">--Please choose an option--</option>
    <optgroup label="animation">
      <option value="toystory">토이스토리</option>
      <option value="zootopia" selected>주토피아</option>
      <option value="insideout">인사이드아웃</option>
    </optgroup>
    <optgroup label="SF">
      <option value="matrix">매트릭스</option>
    </optgroup>
  </select>

  <input type="submit" />
</form>
```

- option을 쓸 때 required를 사용하고 싶을때 value를 빈칸으로 두면 required에서 제외 가능하다.

- legend는 fieldset의 첫번째 자식요소여야 합니다.
