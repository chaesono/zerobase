# TypeScript

- 과거의 TypeScript
  - TypeScript는 JavaScript의 super set이다.
- 현대의 TypeScript

  - TypeScript is javaScript with syntax for types
  - 타입 구문이 존재하는 JavaScript 즉 TypeScript이며 TypeScript가 컴파일되면 JavaScript로 변환된다.

- TypeScript 예시

```ts
type Result = "pass" | "fail";

function verify(result: Result) {
  if (result === "pass") {
    console.log("Passed");
  } else {
    console.log("Failed");
  }
}

// 위의 TypeScript가 컴파일이 되면 해당 JavaScript로 변환된다.
function verify(result) {
  if (result === "pass") {
    console.log("Passed");
  } else {
    console.log("Failed");
  }
}
```

## 타입스크립트 기본 타입

```ts
/**
 * Type Annotation
 */

const val: number = 123;

/**
 * Primitive(원시값)
 * - 불변
 * - 객체가 아닌 값들
 * - 타입 추론을 유도하기 위해 지워도 무방하다.
 */
const str: string = "STRING";
const num: number = 123;
const bool: boolean = true;

/**
 * Object Type(객체 타입)
 */
// any와 다른게 없는 상황
const obj: object = {
  str: "str",
  num: 123,
  child: {
    str: "str",
    num: 123,
  },
};

const obj2: {
  str: string;
  num: number;
  child: {
    str: string;
    num: number;
  };
} = {
  str: "str",
  num: 123,
  child: {
    str: "str",
    num: 123,
  },
};

console.log(obj2.child.str);

/**
 * Function Type(함수타입)
 *
 * 1. 매개변수
 * 2. 반환
 */
function func(num: number, str: string): string {
  return num + str;
}

const func2 = (str1: string, str2: string): void => {
  console.log(str1 + "" + str2);
};

const func3 = (obj: { str1: string; str2: string }): void => {
  console.log(obj.str1 + "" + obj.str2);
};

/**
 * Array Type(배열타입)
 */
const strArr: string[] = ["str", "str2", "str3"];
const strArr2: Array<string> = ["str", "str2", "str3"];

/**
 * Literal Type(리터럴 타입)
 */
let letSTring = "Hello";

const constSTring = "Hello";

/**
 * Typle Type
 *
 * - 길이 고정 & 인덱스 타입이 고정
 * - 여러 다른 타입으로 이루어진 배열을 안전하게 관리
 * - 배열 타입의 길이 조절
 */
const arr: string[] = ["A", "B", "C"];
const tuple: [number, string] = [1, "A"];
const tuple2: [number, ...string[]] = [0, "A", "B", "C"];
const tuple3: (string | number)[] = [0, "A", "B", "C"];

/**
 * undefined null
 *
 * JavaScript에서와 마찬가지로
 * 고유의 특별한 타입으로 인정한다.
 *
 * 이외에 void, never와 같이 더 세밀한 타입도 제공
 *
 * strictNullChecks가 핵심
 */
const nu: null = null;
const un: undefined = undefined;

// 최대한 사용하지 않는 방향으로 설정하고 만약 사용해야한다면
// null or undefined 하나만 사용한다.

/**
 * any type
 *
 * 모든 값(타입)의 집합
 * 절대 사용하지 않는 것이 좋다.
 *
 * noImplicitAny or strict 옵션 true 권장
 */

/**
 * unknown
 *
 * 새로운 최상위 타입
 * any처럼 모든 값을 허용하지만 상대적으로 엄격하다.
 * TS에서 unknwon으로 추론하는 경우는 없으니 개발자가 직접 명시해야함
 * assertion 혹은 타입 가드와 함께 사용한다.
 */

/**
 * void
 *
 * - 함수의 반환이 없는 경우를 명시
 * - 타입 추론에 위임하자
 *
 * JavaScript에서는 암시적으로 undefined 반환
 * 그러나 void와 undefined는 TypeScript에서 같은 것이 아님
 */
```

## TypeScript 클래스

- C#에서 유래된 것이 많다
- 일부 기능은 TS에서만 존재하는 고유 문법으로 컴파일 후에 사라진다.
