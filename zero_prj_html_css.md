# CSS 작성 팁

1. box-sizing: border-box
2. position: relative | absolute | foxed | sticky
3. display: flex | block | inline-block | block
4. margin: 100px
5. padding: 100px
6. width: 100px
7. height: 100px
8. border: 1px solid #000
9. background: #fff
10. font-size: 16px
11. font-weight: 300(thin) | 400(normla) | 500(medium) | 700(bold)
12. color: #000
13. text-align: center | left | right
14. overflow: auto | scroll | hidden
15. z-index: 1
    프로젝트 진행시 이 순서대로 작성하는 것이 좋습니다.

# CSS EMMET

https://docs.emmet.io/cheat-sheet/

- 많이 쓰는 Emmet 예제
  - mt10 : margint-top: 10px;
  - pb10 : padding-bottom: 10px;
  - w100 : width: 100px;
  - h100p : height: 100%;
  - bd : border: 1px sollid #000;
  - bgc : background-color: #fff;
  - fsz10 : font-szie: 10px;
  - fw700 : font-weight: 700;
  - c#ddd : color: #ddd;
  - z10 : z-index : 10;

---

# 핵심 Sass

Sass란?

- Sass(Syntactically Awesome StyleSheets) is a stylesheet language that's complied to CSS

```scss
table {
  table-layout: fixed;
  width: 100%;
  border-collapse: collapse; // table간의 간격을 지워주는 역할
}
```

# project 정리

justify-content

`space-between`
항목은 기본 축을 따라 정렬 컨테이너 내에서 고르게 분포됩니다. 인접한 항목의 각 쌍 사이의 간격은 동일합니다. 첫 번째 항목은 메인 시작 모서리와 같은 높이이고 마지막 항목은 메인 끝 모서리와 같은 높이입니다.

`space-around`
항목은 기본 축을 따라 정렬 컨테이너 내에서 고르게 분포됩니다. 인접한 항목의 각 쌍 사이의 간격은 동일합니다. 첫 번째 항목 앞과 마지막 항목 뒤의 빈 공간은 인접한 항목의 각 쌍 사이 공간의 절반과 같습니다.

`space-evenly`
항목은 기본 축을 따라 정렬 컨테이너 내에서 고르게 분포됩니다. 인접한 항목의 각 쌍, 기본 시작 모서리와 첫 번째 항목, 주요 끝 모서리와 마지막 항목 사이의 간격은 모두 정확히 동일합니다.
