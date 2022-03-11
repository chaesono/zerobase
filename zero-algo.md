# 깊은 복사

- 객체안에 객체가 또 있을 경우 깊은 복사를 사용해야 한다

```js
let user = {
  name: "john",
  age: 23,
  sizes: {
    height: 180,
    wieght: 72,
  },
};
let admin_json = JSON.parse(JSON.strigify(user));
```

# 반복문 제어

- break
  - 반복문 수행 시 코드 블록을 탈출할 때 사용되는 식별자
  - 다중 반복문일 경우 가장 안쪽의 반복문을 종료
  - Label을 통하여 다중 반복문을 한번에 종료 가능
    - Label: 반ㅂ고문 앞에 콜론과 함께 쓰이는 식별자
- continue
  - 반복문 수행시 코드 블록 실행을 해당 라인에서 중지하고 블록 코드를 종료 시킨 후 반복문 내 명시된 조건 판단

# 함수

- 자바스크립트 함수는 매개변수와 인수의 개수가 일치하는지 확인하지 않음
- ES6에서 도입된 기본값을 통해 undefined 변수가 들어올 경우 값 초기화 지정 가능

## 화살표 함수

```js
const add = (x, y) => x + y; // 화살표 함수는 자동으로 return처리 됩니다.
```

# Method

- 객체에 저장된 값이 함수인 경우, 이를 메서드(method)라고 부른다.

## 자리수 표현

- 소수의 자리 수 길이를 제한 : Number.toFixed(pos)
- 정수와 소수의 자리 수를 합한 길이로 제한: Number.toPrecision(pos)

# String

- 문자열 길이 : String.length
- 문자열 접근 : String.charAt(index), String.charCodeAt(index)
- 문자열 검색 : String.indexOf(), String.lastIndexOf(), String.includes(), String.startsWith() 등
- 문자열 변환 : String.toUpperCase(), String.toLowerCase()
- 문자열 치환 : String.replace()
- 문자열 추출 : String.slice(), String.substring(), String.substr()
- 문자열 분할 : String.split()

# 문자열 변환

replace

```js
text.replace(/l/g, "i"); // l을 모두다 i로 바꾼다
text.replace(/l/gi, "i"); // 대소문자 상관없이 l을 모두 i로 바꾼다
```

# 생성자

```js
function FishBread(flavor, price) {
  this.flavor = flavor;
  this.price = price;
  this.base = "flour";
}

let bread_1 = new FishBread("cream", 1200);

console.log(bread_1);
```

# Map

- 다양한 자료형의 key를 허용하고, key-value 형태의 자료형을 저장 가능할 수 있는 Collection
- Map은 Object 대비 비교하면 다양한 key의 사용을 허용하고, 값의 추가/삭제 시 메서드를 통해 수행이 필요함.
- Map을 Object로 변환하는법

```js
let recipe_juice = new Map([
  ["strawberry", 50],
  ["banana", 100],
  ["ice", 150],
]);

console.log(recipe_juice);

let recipe_juice_obj = Object.fromEntries(recipe_juice);
let recipe_juice_kv = Object.entries(recipe_juice_obj);

console.log(recipe_juice_obj);
console.log(recipe_juice_kv);
```

# Set

- value만을 저장하며 중복을 허용하지 않는 Collection

```js
let set = new Set();
let num = new Set([1, 2, 3, 4, 5]);
let str = new Set("Hello!");

console.log(set);
console.log(num);
console.log(str);

set.add(1).add(1).add(10).add(20);
console.log(set);

console.log(set.has(10)); // 값이 있으면 true 없으면 false

set.delete(1);
set.delete(-1); // 없는 value를 지정하더라도 오류는 없고 별도로 반환하는 것은 없다.
```

# 다시 풀어봐야 할 것

47. 기본 문제 풀이 - 무한뺄셈
48. 요일구하기
49. 중복 단어 제거 - Map, Set 차이 다시 생각하기
50. 배열 내 최대값 구하기 : Math.max.apply(null, arr);

# 기본 수학 이론

1. 알고리즘 복잡도

- 시간 복잡도 : 입력 크기의 값에 대해 단위 연산을 몇 번 수행하는지 계산하여, 알고리즘의 수행시간을 평가하는 방법
- 3가지 점근적 표현볍
  - O(빅오) : 최악의 상황을 고려하여 성능 측정 결과 표현
  - 세타 : 평균적인 경우에서의 성능 측정 결과 표현
  - 오메가 : 최선의 상황일 때의 성능 측정 결과 표현
- 걸리는 시간
  - O(log n) = O(1) < O(n) < O(nlogn) < O(N^2) < O(2^n) < O(n!)

2. 경우의 수

- 어떤 사건 혹은 일이 일어날 수 있는 경우의 가짓수를 수로 표현
- 순열 : 서로 다른 n개의 원소 중에서 r개를 중복 없이 골라 순서에 상관 있게 나열하는 경우의 수

```js
// 순열 코드를 짜는방법 1. for 문
// for 문은 순열 개수가 늘어날수록 for문이 늘어나기에 시간복잡도가 크게 증가해 사용하지 않습니다.
let input = ["a", "b", "c"];
let count = 0;

function permutation(arr) {
  // for i -> 첫번째 위치시킬 요소 a, b, c [i, 0, 0]
  for (let i = 0; i < arr.length; i++) {
    // for j -> 두번째 index 위치시킬 요소  [i, j, 0]
    for (let j = 0; j < arr.length; j++) {
      if (i == j) continue;
      // for k -> 세번째 index 위치시킬 요소 [i, j, k]
      for (let k = 0; k < arr.length; k++) {
        if (i == k) continue;
        if (j == k) continue;

        console.log(arr[i], arr[j], arr[k]);
      }
    }
  }
}
permutation(input);
console.log(count);

// 순열 코드를 짜는 방법 2. 재귀
let input = ["a", "b", "c"];
let count = 0;

function permutation(arr, s, r) {
  // 1. 재귀함수를 멈춰야할 조건
  if (s == r) {
    count++;
    console.log(arr);
    return;
  }

  // 2. 재귀를 돌면서 변경되어야 될 부분 / 메인로직
  for (let i = s; i < arr.length; i++) {
    [arr[s], arr[i]] = [arr[i], arr[s]]; // swap
    permutation(arr, s + 1, r)[(arr[s], arr[i])] = [arr[i], arr[s]]; // 원상복귀
  }
}

permutation(input, 0, 2);
console.log(count);
```

// 재귀문 계속 연습해보기

- 조합 : 서로 다른 n개의 원소 중에서 r를 중복 없이 골라 순서에 상관 없이 나열하는 경우의 수

# 배열

메서드

- some() : 배열 내 단 하나라도 콜백 함수의 조건을 만족하는 요소가 있다면 true, 아니면 flase 반환
- every() : 배열 내 모든 요소가 콜백 함수의 조건을 만족한다면 true, 아니면 false 반환 (빈 배열일 경우 true)
