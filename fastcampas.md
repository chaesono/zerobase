## 웹 표준

웹 표준(Web standard)이란 웹에서 사용되는 표준 기술이나 규칙을 의미, W3C의 표준화 제정 단계의 권고안에 해당하는 기술

## 크로스 브라우징

크로스 브라우징이란 조금은 다르게 구동되는 여러 브라우저에서, 동일한 사용자 경험을 줄 수 있도록 제작하는 기술
ex) 크롬 엣지 파이어폭스 오페라 웨일 등에서 같은 경험을 줄 수 있도록 제작하는 기술

## 뷰 포트

웹 페이지가 출력되는 영역

## 웹 이미지

1. 비트맵

- 픽셀이 모여 만들어진 정보의 집합, 레스터 이미지라고도 부름
- 정교하고 다양한 색상을 자연스럽게 표현.
- 확대/축소 시 계단 현상, 품질저하
- png, jpg

2. 벡터

- 점, 선, 면의 위치, 색상 등 수학적 정보의 형태로 이루어진 이미지
- 확대/축소에서 자유로움, 용량 변화가 없음
- 정교한 이미지(인물, 풍경 사진 같은)를 표현하기 어려움.
- svg

## 기호

' 그레이브
~ 틸드
! exclamation mark
@ at sign 골뱅이
'#' sharp
^ caret 캐럿
& Ampersand 엠퍼센드
'\*' Asterisk 별표시
'-' 하이픈, 대시 Hyphen, Dash
\_ Underscore, Low dash
| vertical bar
() parenthesis 퍼렌서시스
{} brace
[] bracket
<> angle bracket

cmd + b : 사이드바 열고 닫기
cmd + p : 빠른 열기
cmd + shift + p : 모든 명령 열기
cmd + shift + f : 찾기 바꾸기
alt + up : 줄이동
alt + shift + down : 줄 복사
cmd + l : 화면 분할

head는 정보를 나타냄

## css, js 연결하기

css는 link로 js는 script로

## 정보를 의미하는 태그 살펴보기

1. <title> : HTML 문서의 제목을 정의
2. <link rel="stylesheet" href="./main.css"> : rel은 가져올 무넛와 관계 href는 가져올 문서의 경로, 외부 문서를 가져와 연결할 때 사용(대부분 CSS 파일)
3. favicon = Favorite Icon, HTML Favicon를 적용할 때는 이름을 favicon이라고 지정하시길 권장하며, favicon,ico or favicon.png 파일이 주로 사용됩니다.
4. <style> : CSS를 HTML 문서 안에서 작성하는 경우에 사용
5. <script> : src를 설정하여 파일을 가져오거나, 문서안에서 직접 작성도 가능
6. <meta charset="UTF-8"> : 문자 인코딩 방식
   <meta http-equiv="author" content="Sono">
   <meta name="viewport" content="width=, initial-scale=1.0">
   : meta는 HTML 문서의 제작자, 내용, 키워드 같은, 여러 정보를 검섹엔진이나 브라우저에게 제공

## 상대경로와 절대경로

1. 상대경로
   ./ (생략가능)
   ../

2. 절대경로
   http(https)
   /(//)

## Codepen.io

현재작업하는 내용중에서 몇개를 추가하여 실험하고 싶을때 사용하는 사이트

## 브라우저 스타일 초기화

https://www.jsdelivr.com/package/npm/reset-css

## HTML 기본 문법

요소 : <시작(열린)태그>내용</종료(닫힌)태그>

## 글자(인라인 요소)와 상자(블록 요소)

<span> : 대표적인 인라인요소 본질적으로 아무것도 나타내지 않는, 콘텐츠 영역을 설정하는 용도.
인라인 요소는 글자 요소이기에 가로 세로 사이즈를 지정할 수 없다.
글자는 위아래 여백이 불가능하다 좌우는 가능하다.
인라인 요소는 자식에 블록요소를 넣을 수 없다.

<div> : 대표적인 블록 요소 본질적으로 아무것도 나타내지 않는, 콘텐츠 영역을 설정하는 용도
가로 너비는 최대한 늘어나려 함
가로 세로 사이즈 지정 가능
블록 요소는 자식에 블록요소 인라인요소 다 넣을 수 있다.

## HTML 핵심 요소 정리

<div> : 블록 요소 - 특별한 의미가 없는 구분을 위한 요소
<h1> : 블록 요소 - 제목을 의미하는 요소
<p> : 블록 요소 - 문장을 의미하는 요소 (paragraph)
<img> : 인라인 요소 : 이미지를 삽입하는 요소
<a href="" target=""> : 인라인 요소 - 다른/같은 페이지로 이동하는 하이퍼링크를 지정하는 요소(Anchor) target은 새탭일지 새창일지 정하는 요소
<input> : inline-block요소 - 사용자가 데이터를 입력하는 요소
input 에서 value요소는 미리 입력된 값을 지정할수 있으며 placeholder요소는 힌트를 설정해둘수 있다 disabled로 비활성화 할수도 있다.

## CSS 기본 문법

선택자 {속성: 값;}
ex)
div {
color: blue;
}

## CSS 선언 방식

1. 내장 방식
   - <style>의 내용으로 스타일을 작성하는 방식
2. 링크 방식
   - <link rel="stylesheet" href="./css/main.css">
   - 병렬로 연결
3. 인라인 방식
   - <div style="color: red;"></div>
4. @import 방식
   - @import url("./box.css")
   - 직렬로 연결

## CSS 선택자

1. 기본
   - \*(전체 선택자) : 모든 요소를 선택.
   - 태그 선택자 : 태그이름이 요소 선택
     ex) li, div, span
   - 클래스 선택자 : class 속성의 값이 요소 선택
     ex) .orange {
     color: red;
     }
   - 아이디 선택자 : id 속성의 값이 요소 선택
     ex) #orange {}
2. 복합
   - 일치 선택자
     - ABCXYZ : 선택자 ABC와 XYZ를 동시에 만족하는 요소 선택.
       ex) span.orange {} - span과 orange클래스를 동시에 만족하는 곳에 적용
   - 자식 선택자
     - ABC > XYZ : 선택자 ABC의 자식 요소 XYZ 선택.
       ex) ul > .orange {} - ul의 자식요소인 li중 클래스가 orange것을 선택
   - 하위 선택자
     - ABC XYZ : 선택자 ABC의 하위 요소 XYZ 선택. 띄어쓰기가 선택자의 기호
       ex) div .orange {}
   - 인접 형제 선택자
     - ABC + XYZ : 선택자 ABC의 다음 형제 요소 XYZ 하나를 선택.
       ex) .orange + li {}
   - 일반 형제 선택자
     - ABC ~ XYZ : 선택자 ABC의 다음 형제 요소 XYZ 모두를 선택.
       ex) .orange ~ li {}
3. 가상 클래스
   - 행동을 했을 때 동작하는 개념
   - hover : 마우스를 올렸을 때 바뀌는 행동
     ex) a:hover {}
   - active : 마우스를 클릭하고 있는 동안 바뀌는 행동
     ex) a:active {}
   - focus : 포커스가되면 선택.
     - 포커스가 될 수 있는 요소는 HTML 대화형 콘텐츠가 해당합니다. input, a, button, label, select 등 여러 요소가 있습니다. 그리고 HTML 대화형 콘텐츠 요소가 아니더라도, tabindex 속성을 사용한 요소도 Focus가 될 수 있습니다. 구글 검색: HTML 대화형 콘텐츠 mdn
       ex) input:focus {}
       ex) <div tabindex="-1">을 설정하면 focus가 될 수 있다.
   - FIRST CHILD
     - ABC:first-child : 선택자 ABC가 형제 요소 중 첫째라면 선택.
       ex) .fruits span:first-child {}
   - LAST CHILD
     - ABC:last-child
   - NTH CHILD
     - ABC:nth-child(n) : 선택자 ABC가 형제 요소중 n째라면 선택.
       ex) .fruits \*:nth-child(2n) {} n은 0부터 시작
   - 부정 선택자
     - ABC:not(XYZ) : 선택자 XYZ가 아닌 ABC 요소 선택
       ex) .fruits \*:not(span) {}
4. 가상 요소

- BEFORE
  - ABC::before : 선택자 ABC 요소의 내부 앞에 내용(Content)을 삽입
    ex) .box::before {content: "앞!"}
- AFTER
  - ABC::after : 선택 요소의 내부 뒤에 내용을 삽입
    Ex) .box::after {}
- BEFORE와 AFTER는 content를 추가하지않더라도 content: ""를 작성해야 한다
- 인라인요소로 추가됩니다.
- 인라인요소를 블록요소로 바꿔주려면 display: block; 을 추가합니다.

5. 속성 선택자

- ATTR
  - [ABC] : 속성 ABC을 포함한 요소 선택
    ex) [disabled] {} : disabled 속성이 있는 곳에 적용
    ex) [type] {} : input의 경우에는 type을 무조건 갖고있기에 다 적용 됩니다.
- ATTR=VALUE
  - [ABC="XYZ"] : 속성 ABC을 포함하고 값이 XYZ인 요소 선택.
    ex) [type="password"] {} : type이 password인 요소를 선택

## 스타일 상속

- 상속되는 CSS 속성은 모두 글자/문자 관련 속성들 입니다.
  ex) font-style, font-weight, font-size, line-height, font-family, color, text-align 등등
- 강제상속
  - 상속이 되지않는 CSS 내용도 강제적으로 상속을 할 수있게 하는 것
    ex) height: inherit;

## 선택자 우선순위

{color: red !important;} : important는 1순위
인라인선언 : 1000점 Ex) style="color: orange;"
id 선택자 : 100점 ex) #box
class 선택자 : 10점 ex) .box
태그 선택자 : 1점 ex) div {}
전체 선택자 0점 ex) \* {}

용어가 중요하지않지만 이러한 점수를 명시도 라고 합니다.

## CSS 속성

1. 너비(width, height)

- auto : 기본값(요소에 이미 들어있는 속성의 값) 브라우저가 자동으로 너비를 계산
- 단위 : px, em ,vw 등 단위로 지정
- 인라인요소는 가로사이즈를 최대한 줄이려하고 블록요소는 최대한 늘리려한다.
- max-width, max-height : 요소가 커질 수 있는 최대 가로세로 너비
  - none : 최대 너비 제한 없음
  - 단위 : px, em ,vw 등 단위로 지정
- min-width, min-height : 요소가 작아질 수 있는 최소 가로세로 너비
  - 0 : 최소 너비 제한 없음
  - 단위 : px, em, vw 등 단위로 지정

2. 단위
   px : 픽셀
   % : 상대적 백분율
   em : 요소의 글꼴 크기
   rem : 루트 요소의 글꼴 크기
   vw : 뷰포트 가로 너비의 백분율
   vh : 뷰포트 세로 너비의 백분율

3. 외부 여백(margin)

- margin : 음수도 사용 가능
  - 0 : 외부 여백 없음
  - auto : 브라우저가 여백을 자동으로 계산
  - 단위 : px, em, vw 등 단위로 지정

4. 내부 여백(padding)

- padding : 요소의 내부 여백을 지정하는 단축 속성
  - 0 : 내부 여백 없음
  - 단위 : px, em, vw 등 단위로 지정
  - % : 부모 요소의 가로 너비에 대한 비율로 지정

5. 테두리 선(border)과 색상 표현

- border : border-width 두께, border-style 종류, border-color 색상
- 기본값 : border: mideum none black;

- border-style

  - solid : 실선
  - dashed : 파선 - - - - - -
  - dotted : 점선
  - double : 두 줄 선

- border-color

  - black : 검정색
  - transparent : 투명

- border-radius : 모서리 둥글게

  - 0 : 둥글게 없음
  - 단위 : px, em ,vw

- box-sizing : 요소의 크기 계산 기준을 지정
  - content-box(기본 값) : 요소의 내용으로 크기 계산
  - border-box :요소의 내용 + padding + border로 크기 계산
    Ex) box-sizing: border-box;

6. overflow

- 요소의 크기 이상으로 내용이 넘쳤을 때, 보여짐을 제어하는 단축 속성
  - visible : 넘친 내용을 그대로 보여줌
  - hidden : 넘친 내용을 잘라냄
  - scroll : 넘친 내용을 잘라냄, 스크롤바 생성
  - auto : 넘친 내용이 있는 경우에만 잘라내고 스크롤바 생성

7. 출력 특성

- display
  - block : 상자 요소
  - inline : 글자 요소
  - inline-block : 글자 + 상자 요소
  - flex : 플렉스 박스 (1차원 레이아웃)
  - grid : 그리드 (2차원 레이아웃)
  - none : 보여짐 특성 없음, 화면에서 사라짐
  - 기타 : table, table-row, table-cell 등 ...

8. 투명도

- opacity

9. 글꼴

- font-style : 글자의 기울기

  - normal : 기울기 없음
  - italic : 이텔릭체

- font weight : 글자의 두께

  - normal, 400 : 기본 두께
  - bold, 700 : 두껍게
  - 100~900 : 100단위의 숫자 9개, 일반적으로 normal과 bold를 사용함

- font-size : 글자의 크기

  - 16px : 기본 크기

- line-height : 한 줄의 높이

  - 숫자 : 요소의 글꼴 크기의 배수로 지정
  - 단위 : px, em, rem

- font-family : 글꼴 지정
  - serif : 바탕체
  - sans-serif : 고딕체
  - monospace : 고정너비 글꼴 계열

10. 문자

- color : 글자의 색상
- text-align : 문자의 정렬 방식
- text-decoration : none, underline, line-through(중앙 선)
- text-indent : 문자 첫 줄의 들여쓰기

11. 배경

- background-color : 배경의 색상 기본값 transpaerent(투명함)
- background-image : url("경로")
- background-repeat : 배경 이미지 반복
- background-position : 배경 이미지 위치
- background-size : 배경 이미지 크기 cover(비율을 유지, 요소의 더 넓은 너비에 맞춤), contain(비율을 유지, 요소의 더 짧은 너비에 맞춤)
- background-attachment : 배경 이미지 스크롤 특성 scroll(이미지가 요소를 따라서 같이 스크롤), fixed(이미지가 뷰포트에 고정, 스크롤 X)
-

12. 배치

- position : 요소의 위치 지정 기준
  - static : 기준 없음
  - relative : 요소 자신을 기준
  - absolute : 위치 상 부모 요소를 기준
  - fixed : 뷰포트를 기준
  - sticky : 스크롤 영역 기준
- top, botton, left, right : 요소의 각 방햘별 거리 지정

- 요소 쌓임 순서

  - 어떤 요소가 사용자와 더 가깝게 있는지 결정
    1. 요소에 postion 속성의 값이 있는 경우 위에 쌓임.(기본 값 static 제외)
    2. 1번 조건이 같은 경우, z-index 속성의 숫자 값이 높을 수록 위에 쌓임.
    3. 1번과 2번 조건까지 같은 경우, HTML의 다음 구조일 수록 위에 쌓임 = HTML에서 더 나중에 작성 된 것이 위에 쌓임.

- z-index : 요소의 쌓임 정도를 지정

  - z-index: auto(부모 요소와 동일한 쌓임 정도) = 0
  - z-index: 숫자(숫자가 높을 수록 위에 쌓임)

- position 속성의 값으로 absolute, fixed가 지정된 요소는, display 속성이 block으로 변경됨.

13. 플렉스 Container

- display : Flex Container의 화면 추력 특성(컨테이너를 기준)
  - display: flex = 블록요소들은 수직으로 쌓이는데 플렉스를 설정해주면 수평으로 바뀐다.
  - display: inline-flex = 인라인 요소와 같이 Flex Container 정의
- flex-direction : 주 축을 설정(수평, 수직)
  - row : 기본값 행 축(좌 > 우)
  - row-reverse : 행 축 (우 > 좌)
  - column : 위 > 아래
  - column-reverse : 아래 > 위
- flex-wrap : Flex Items 묶음(줄 바꿈) 여부
  - nowrap : 묶음 없음
  - wrap : 여러 줄로 묶음
  - wrap-reverse : wrap의 반대 방향으로 묶음
- justify-content : 주 축의 정렬 방법(수평정렬)
  - flex-start : Flex Items를 시작점으로 정렬
  - flex-end : Flex Items를 끝점으로 정렬
  - center : Flex Items를 가운데 정렬
- align-content : 교차 축의 여러 줄 정렬 방법(수직정렬)
  - stretch : Flex Items를 시작점으로 정렬
  - flex-start : Flex Items를 시작점으로 정렬
  - flex-end : Flex Items를 끝점으로 정렬
  - center : Flex Items를 가운데 정렬
- align-items : 교차 축의 한 줄 정렬 방법
  - stretch : 기본값 Flex Items를 교차 축으로 늘림
  - flex-start : Flex Items를 시작점으로 정렬
  - flex-end : Flex Items를 끝점으로 정렬
  - center : Flex Items를 가운데 정렬

## 플렉스 Items

- order : Flex Item의 순서
  - 0 : 순서없음 (기본값)
  - 숫자 : 숫자가 작을수록 먼저
- flex-grow : Flex Item의 증가 너비 비율
  - 0 : 증가 비율 없음 (기본값)
  - 숫자 : 증가 비율
- flex-shrink : Flex Item의 감소 너비 비율
  - 1 : Flex Container 너비에 따라 감소 비율 적용(기본값)
  - 숫자 : 감소 비율
- flex-basis : Flex Item의 공간 배분 전 기본 너비
  - auto : 요소의 Content 너비 (기본값)
  - 단위 : px, em, rem 등 단위로 지정

## 전환

- transition : 요소의 전환 효과를 지정하는 단축 속성
  - transition: 속성명 지속시간 타이밍함수 대기시간;
  - transition-property : 속성명
    - all : 모든 속성에 적용, 기본 값
    - 속성이름 : 전환 효과를 사용할 속성 이름 명시
  - transition-duration : 지속시간, 지속시간은 필수로 작성해야 함
    - 0s : 전환 효과 없음, 기본값
    - 시간 : 지속시간을 지정
  - transition-timing-function : 타이밍함수
    - ease : 느리게 - 빠르게 - 느리게
    - linear : 일정하게
    - ease-in : 느리게 - 빠르게
    - ease-out : 빠르게 - 느리게
    - ease-in-out : 느리게 - 빠르게 - 느리게
  - transition-delay : 대기시간
    - 0s : 대기시간 없음, 기본값
    - 시간 : 대기시간을 설정

## 변환 : transform

transform : 변환함수

- 2D 변환 함수
  - translate(x,y) : 이동(x축 ,y축)
  - translateX(x)
  - translateY(y)
  - scale(x, y) : 크기(x, y)
  - rotate(degree) : 회전
  - skewX(x) : 기울임(x축)
  - skewY(y) : 기울임(y축)
- 3D 변환 함수
  - perspective(n) : 원근법(거리) - 제일 앞에 작성해야 함
    - perspective: 600px; - 관찰 대상의 부모에 적용
      - 기준점 설정 : perspective-origin
    - transform: perspective(600px); - 관찰 대상에 적용
      - 기준점 설정 : transform-origin
  - rotateX(x) : 회전(x축)
  - rotateY(y) : 회전(y축)
  - backface-visibility : 3D 변환으로 회전된 요소의 뒷면 숨김 여부
    - visible : 뒷면 보임, 기본값
    - hidden : 뒷면 숨김

### JS 선행

## 표기법

- dash-case(kebab-case) : HTML, CSS에서 주로 쓰임
  - the-quck-brown-fox-jumps-over-the-lazy-dog
- snake_case : HTML, CSS
- camelCase : JS
  - theQuickBrownFoxJumpsOverTheLazyDog
- PascalCase : JS
  - TheQuickBrownFoxJumpsOverTheLazyDog
- Zero-based Numbering : 0 기반 번호 메기기, 특수한 경우를 제외하고 0부터 숫자를 시작

## 보간법

- 문자형
  let myName = "HEROPY";
  let hello = `Hello ${myName}?!`

- Undefined : 값이 할당되지 않은 상태를 나타냅니다.
  let undef;
  let obj = {abc: 123};
  console.log(undef); // undefined
  console.log(obj.abc); // 123
  console.log(obj.xyz); // undefined

- 객체 데이터(Object) : 여러 데이터를 Key:Value 형태로 저장합니다.
  let user = {
  name: 'HEROPY',
  age: 85,
  isValid: true
  }
  console.log(user.name)

## 변수 : 데이터를 저장하고 참조하는 데이터의 이름, var, let, const

- let : 재사용이 가능
  let a = 2;
  let b = 5;
  a = 100; 재할당도 가능
  console.log(a+b);

- const : 재할당 불가능

## 예약어 : 특별한 의미를 가지고 있어, 변수나 함수 이름 등으로 사용할 수 없는 단어 : Reserved Word

- this, if, break 등

## 함수 : 특정 동작을 수행하는 일부 코드의 집합 function

```js
// 함수 선언
function helloFunc() {
  // 실행 코드
  console.log(1234);
}
// 함수 호출
helloFunc(); // 1234
```

## 객체 데이터

```js
const heropy = {
  name: "HEROPY",
  age: 85,
  // Method
  getName: function () {
    return this.name;
  },
};

console.log(heropy, getName());
```

## DOM API : Document Object Model, Applcation Programming Interface

- 쉽게 말하면 DOM 은 HTML의 내용들을 의미하며, API는 명령을 의미한다.
- 브라우저는 코드를 위에서 아래로 읽어가기에 단순히 head 부분에 script를 선언하면 내용을 뭔지 모르는상태에서 js를 실행하기에 defer를 선언해주거나 script를 body 후미에 선언해준다. 하지만 정보를 알려주는 부분은 head에 속하는 것이 좋기때문에 defer를 선언해주는이 옳은 방법이다.

```js
// HTML 요소(Element) 1개 검색/찾기
const boxEl = document.querySelector(".box");

// HTML 요소에 적용할 수 있는 메소드
boxEl.addEventListener();

// 인수(Arguments)를 추가 기능
boxEl, addEventListener(1, 2);

// 1 - dlqpsxm(Event, 상황)
boxEl.addEventListener("click", 2);

// 2 - 핸들러(Handler, 실행할 함수)
boxEl,
  addEventListener("click", function () {
    console.log("Cllick!");
  });
```

```js
// HTML 요소(Element) 1개 검색/찾기
const boxEl = document.querySelector(".box");

// HTML 요소에 적용할 수 있는 메소드
boxEl.classList.add("active");
let isContains = boxEl.classList.contains("active");
console.log(isContains); // true

boxEl.classList.remove("active");
isContains = boxEl.classList.contains("active");
console.log(isContains); // false
```

```js
// HTML 요소(Element) 모두 검색/찾기
const boxEls = document.querySelectorAll(".box");
console.log(boxEls);

// 찾은 요소들 반복해서 함수 실행
// 익명 함수를 인수로 추가
boxEls.forEach(function () {});

// 첫 번째 매개변수(boxEl): 반복 중인 요소
// 두 번째 매개변수(index): 반복 중인 번호
boxEls.forEach(function (boxEl, index) {});

// 출력
boxEls.forEach(function (boxEl, index) {
  boxEl.classList.add(`order-${index + 1}`);
  console.log(index, boxEl);
});
```

```js
const boxEl = document.querySelector(".box");

// Getter, 값을 얻는 용도
console.log(boxEl.textContent); // Box!!

// Setter, 값을 지정하는 용도
boxEl.textContent = "HEROPY?!";
console.log(boxEl.textContent); // HEROPY?!
```

## 메소드 체이닝

```js
// split: 문자를 인수 기준으로 쪼개서 배열로 반환.
// reverse: 배열을 뒤집기.
// join: 배열을 인수 기준으로 문자로 병합해 반환.

const a = "Hello~";
const b = a.split("").reverse().join(""); // 메소드 체이닝...
```

### 오픈그래프

웹페이지가 소셜 미디어(페이스북 등)로 공유될 때 우선적으로 활용되는 정보를 지정합니다.

###

인라인요소는 baseline을 넘어서 밑에 살짝 여백이 생길 수 있으니 img같은경우 css에 display: block을 설정해주면 여백이 사라진다.

a태그를 사용할 때 당장 주소를 정하지 않았다면 href="#" or href="javascript:void(0)" 을 설정해준다.

## BEM(Block Element Modifier) : HTML 클래스 속성의 작명법

- 요소\_\_일부분 : Underscore 기호로 요소의 일부분을 표시
- 요소--상태 : Hyphen 기호로 요소의 상태를 표시

## scroll

lodash cdn 검색후 복사

window.addEventListener('scroll', \_.throttle(function () {
console.log('scroll')
}, 300));

.3초마다 실행할 수 있게 해주는 코드

## 애니메이션 라이브러리

gsap cdn

---

# JS

## IIFE - Immediately-Invoked Function Expression : 즉시실행함수

```js
const a = 7;
function double() {
  console.log(a * 2);
}
double();

// 즉시실행함수
(function () {
  console.log(a * 2);
})();

(function () {
  console.log(a * 2);
})();
```

---

## 호이스팅(Hoisting) : 함수 선언부가 유효범위 최상단으로 끌려올려지는 상황

```js
double();

function double() {
  console.log(a * 2);
}
```

## 타이머 함수

- setTimeout(함수, 시간) : 일정 시간 후 함수 실행
- setInterval(함수, 시간) : 시간 간격마다 함수 실행
- clearTimeout() : 설정된 Timeout 함수를 종료
- clearInterval() : 설정된 Interval 함수를 종료

## this

- 일반 함수는 호출 위치에서 따라 this 정의
- 화살표 함수는 자신의 선언된 함수 범위에서 this 정의

## ES6 Classes

```js
class User {
  constructor(first, last) {
    this.firstName = first;
    this.lastName = last;
  }
  getFullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```

## 데이터 불변성(Immutability)

- 원시 데이터 : String, Number, Boolean, undefined, null
  - 값이 같으면 같은 것이라고 봐도된다. 처음에 4라는 값을 1번주소에 할당하였다면 새로운 4라는 값을 할당할 때 새로운 주소에 할당되는 것이 아니고 기존 주소에 할당되는 것이기 때문이다.
- 참조형 데이터 : Object, Array, Function
  - 값이 같다고 해도 주소가 다르기에 같다고 할수가 없다.

## 얕은 복사, 깊은복사

```js
const user = {
  name: 'Heropy',
  age: 85,
  emails: [codnjswls12@naver.com]
}
const copyUser = user
console.log(copyUser === user)
// true

user.age = 22
// 이렇게 하였을 시 copyUser의 age도 의도치 않게 22가 되버린다.
// 그렇기에 복사를 하려면 다르게 설정해주어야 한다
const copyUser = user // 이 부분을
const copyUser = Object.assign({}, user) // 이렇게 수정해주면 된다. 또는 : 얕은 복사
const copyUser = {...user} // 이렇게 설정해주어도 된다. : 얕은복사
```

- 깊은복사

```js
import _ from "lodash";

const copyUser = _.cloneDeep(user); // 깊은 복사
```
