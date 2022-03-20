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

# CSS

1. Attribute selector

```html
<a href="https://example.com" target="_blank"></a>
```

```css
/* 1. [attr] */
a[target] {
  color: hotpink;
}

/* 2. [attr=value] */
a[href="https://example.com"]
{
  color: indigo;
}
/* 3. [attr^=value] */
a[href^="http"]: a라는 태그에서 http로 시작하는 애들을 선택 {
  color: indigo;
}
/* 4. [attr$=value] */
a[href$="http"]: http로 끝나는애들을 선택 {
  color: indigo;
}
/* 5. [attr*=value] */
a[href*="example"]: example을 가지고만 있으면 선택 {
  color: indigo;
}
```

2. Pseudo-Class Selector

```css
/* 1. first-child */
li:first-child {
  color: green;
}

/* 2. last-child */
span:last-child {
  color: tomato;
}

/* 3. nth-child */
li:nth-child(3) {
  color: pink;
}

/* 4. first-of-type */
p:first-of-type {
  // p형제들 중에 첫 번째
  color: red;
}

/* 5. last-of-type */
/* 6. nth-of-type() */

/* 7. :not() */
input:not(.pw) {
  // input을 고르는데 pw를 클래스로 가진 것을 제외한 모든 것을 선택
  background-color: indianred;
}

/* 8. link */
a:link {
  // 방문한 적 없을 때의 링크 색
  color: tomato;
}
/* 9. visited */
a:visited {
  // 방문했던 링크의 색
}

* link > visited > hover > active 순서로 css를 작성한다.
/* 10. hover */ : 마우스를 올렸을 때
/* 11. active */ : 마우스를 클릭했을 때
/* 12. focus */ : 선택 되었을 때 해당하는 곳의 css 지정
/* 13. enabled */
/* 14. disabled */
/* 15. checked */
```

3. Pseudo-Element Selector(가상 요소 선택자)

- 가상 요소 선택자는 selector::~~ 더블 콜론을 쓴다.
  하지만 콜론을 하나도 사용해도 되긴하지만 가상 클래스 선택자와 구분하기 위해 더블 콜론으로 작성한다.

```css
/* 1. before, after */
: css에서 지정하는 가상 요소, 꾸밈을 위한 요소
.favorite::before {
  content: "*";
  color: indianed;
}

.favorite::after {
  content: "*";
  color: indianed;
}

/* 2. first-letter, first-line, selection */
- 첫번 째 글자, 첫번째 라인
- selection: 선택 영역을 의미합니다 예를 들어 밑의 코드에 해당한 부분을 드래그하면 해당 css가 적용됩니다.
.lorem::selection {
  bacground-color: red;
  color: white:
}
```

4. 선택자 결합

```css
/* 하위 선택자 */
/* ul에 속한 li들중 마지막 요소 */
ul li:last-of-type {
  color: red;
}

/* 자식 선택자 */
/* #list의 자식들 중에서만 고른 마지막 요소 */
#list > li:last-of-type {
}

/* 형제 선택자 */
/* 1. 일반 형제 선택자 결합 (~) */
/* selector는 code의 뒤에있는 선택자만 가능하며 같은 부모를 가지고 있어야 한다. 
쉽게 말해 code의 뒤쪽에 있는 Selector를 바꾸는데 용이하다. */
code ~ selector {
}

/* 2. 인접 형제 선택자 결합 (+) */
/* - 말 그대로 인접한 위아래 selector 만 선택이 가능합니다.  */
code + selector {
}

/* 3. 그룹화 */
p,
span,
div {
  color: puple;
}
```

5. 범용 선택자(Universal Selector)

```css
/* 모든 요소 */
* {
}

/* p 태그 중 class로 red를 가진 오소 */
p.red {
}
```

6. 상속 제어하기 - initial. inherit, unset

```css
.parent {
  color: blue;
}

/* 원래 parent의 css를 상속받지만 initial을 설정하면 기존의 설정이 유지된다.
하지만 모든 요소가 상속되는 것은 아니다.
all의 경우는 전부다 initial을 설정한다. */
.child {
  color: initial;
  font-size: initial;

  all: initial;
}

/* initial과는 다르게 상속 시키게해주는 요소 */
.parent * {
  color: inherit;
}

/* unset
1. 부모로부터 상속받을 값이 있을 때 : inherit로 적용됩니다.
2. 부모로부터 상속받을 값이 없을 때 : initial로 적용됩니다. */
.parent2 .child1 {
  all: unset;
}
```

6. 우선순위
   선언된 곳 > 명시도 > 코드 위치

선언된 곳

명시도 (적용범위가 적을수록 명시도가 높은 것!)
id가 class보다 명시도가 높다.

코드 위치

!important를 입력하면 가장 높은 우선순위이다.

# Font

```css
/* font의 단축속성을 쓸시 */
font: style weight size/lien-height font-family 순서로 작성하여야 합니다.;
```

# SCSS

```scss
// input의 type이 text이고 input의 클래스가 error일때 바로 인접한 error-msg가 color가 red다.
input[type="text"] {
  &.error + .error-msg {
    color: red;
  }
}
```

```css
/* button의 hover가 disabled일때는 작동하지 않는다. */
button:not(:disabled):hover {
  background-color: red;
}
```

## 단위와 값

- 절대길이 : px
- 상대길이 : em, rem, vw, vh, vmin, vmax
- em : 부모의 font-size
- rem : 1rem = root의 font-size

font-size는 em, rem등 상대길이로 설정하는 것이 좋다.

- vw, vh : 뷰포트 백분율 길이
- vmin, vmax : vw, vh중 작은 것이 vmin 큰것이 vmax : 보통 가로모드, 세로모드를 대응해야할 사이트를 만들 때 사용합니다.

## 함수 표기법

- calc()

```
width: calc(100% - 50px);
```

- min()

```
<!-- 둘중 작은 값 선택 -->
width: min(100%, 500px);
```

- max()
<!-- 둘중 큰 값 선택 -->

```
width: max(100%, 500px);
```

---

## margin collapsing

- 마진 상쇄, 마진 겹침, 마진 중복 등등 으로 불리운다
- 여러 블록요소들의 위/아래 margin이 경우에 따라 가장 큰 크기를 가진 margin으로 결합되는 현상
- 아래의 3가지 경우에 일어난다
  - 인접 형제
    - 두 형제 요소의 위/아래 여백이 만나 상쇄된다.
  - 부모-자식요소 간
    - 부모 블록에 border, padding, inline content가 업ㅅ어서 부모와 자식의 margin-top이 만나는 경우
    - 부모 블록에 border, padding, inline content가 없고, 부모-자식을 분리할 height값이 지정되지 않아 부모와 자식이 margin-bottom이 만나는 경우
  - 빈 블록
    - border, padding, content가 없고, height 또한 존재하지 않으면, 해당 블록의 margin-top과 margin-bottom이 상쇄된다.

---

# 레이아웃

```css
/* 
레이아웃

display - inline, block, inline-block
*/

/* 
inline 요소 : ex) span..
  - 영역의 크기가 내부 콘텐츠 크기로 정해진다.
  - margin, padding을 좌우는 지정할수 있지만, top/bottom을 지정할 수 없다.
  - 여러 요소가 가로 배치가 된다.

block 요소 : ex) div..
  - 영역의 크기를 width, height 지정할 수 있다.
  - width를 지정하지 않으면 가로 전체를 차지한다.
  - 여러 요소가 세로 배치가 된다.

inline-block 요소 : ex) input..
  - 영역의 크기를 width, height 지정할 수 있다.
  - 여러 요소가 가로배치가 된다.
  
 */

/* 
 요소를 없애는 방법
 display: none,
 visibility: hidden
 */
```

## float

- CSS 속성 float 은 한 요소가 보통 흐름(normal flow)으로부터 빠져 텍스트 및 인라인 요소가 그 주위를 감싸는 자기 컨테이너의 좌우측을 따라 배치되어야 함을 지정합니다.

## position

- position: static; : 기본 값
- position: relative; : 자기 자신을 기준
- position: absolute; : 현 위치의 부모를 기준
  - 문서의 흐름에서 제거된다.
  - 조상 중에서 position이 static이 아닌 요소를 찾아 기준점을 삼는다.
- position: fixed
  - 문서의 흐름에서 제거된다.
  - 뷰포트의 초기 컨테이닝 블록을 기준으로 삼는다.
- position: sticky;
  - 스크롤할때 fixed처럼 작동
  - 스크롤되는 조상의 바로 하위에 적용시켜야한다.
  - 조상의 자식의 자식에 설정하면 동작하지 않는다.

---

# Flex, Grid 항상 공부하기
