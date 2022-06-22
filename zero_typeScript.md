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
- 일부 기능은 Ts에서만 존재하는 고유 문법으로 컴파일 후에 사라진다.

```Ts
/**
 *  Class
 */
class Person {
    /**
     * 필드
     *
     * - 일종의 속성
     * - public으로 사용 가능합니다.
     */
    name: string;
    age: number;
    readonly location: string = 'Korea'; // readonly는 수정 불가능함

    /**
     * 생성자
     *
     * - 초기화를 담당
     */
    constructor(name: string, age: number) {
        this.name = name
        this.age = age
    }

    /**
     * 메서드
     *
     * 객체(클래스)에서는 행동을 뜻한다.
     */
    introduce(): string{
        return `${this.name}의 나이는 ${this.age}입니다.`
    }
}

/**
 * 인스턴스
 *
 * - 클래스에서 파생된 고유한 것
 * - 실제로 생성된 후 메모리에 올라감
 */
const p = new Person('Jang', 99);

console.log(p.introduce())
```

## Getter & Setter

```ts
/**
 *  Getter & setTranslate
 *
 *  필드에 접근할 권한ㅇ르 가진 제어자
 *
 *  getter O / setter X => 속성은 자동으로 읽기 전용
 *  setter 매개변수의 타입 X / getter의 반환 타입에서 추론
 *
 *  private 속성은 .연산자로 접근할 수 없다.
 */
class Person {
  name: string;
  private _age: number; // private을 사용하면 다른곳에서 age를 사용하지 못합니다.

  constructor(name: string, age: number) {
    this.name = name;
    this._age = age;
  }

  // getter를 사용하면 age를 볼수 있습니다.
  get age() {
    return this._age;
  }

  set age(age) {
    this._age = age;
  }
}

const p = new Person("Jang", 99);

console.log(p.age);
```

## extends

```ts
/**
 * extends
 * - 상속으로 바라 볼 것인가 확장으로 바라 볼 것인가 고민해보기
 * - 상속
 * - 확장
 */
class 기본 {
  result() {
    return "Base";
  }
}

// 부모클래스를 상속 받음
class 파생 extends 기본 {
  result() {
    return "Derived";
  }
}

const de = new 파생();

console.log(de.result());
```

## super

```ts
/**
 * super
 *
 * 기본 클래스 호출시 사용
 * 생성자에서 this 사용 전 호출되어야함
 */
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  sayName() {
    return `동물의 이름은 ${this.name}`;
  }
}

class Person extends Animal {
  constructor(name: string) {
    super(name);
  }

  sayName() {
    return `사람의 이름은 ${this.name}`;
    // return super.sayName() 상위 클래스의 메서드를 접근할 때
  }
}

const person = new Person("Sono");

console.log(person.sayName());
```

## 접근 제어자

- 속성과 메서드에 접근을 제한할 수 있다.
- 클래스 내부 구현 정보를 적당히 공개하여 일부분만 노출시킨다
  - API와 비슷한 흉내를 낼 수 있다.
  - 타입 시스템을 이용해 규칙을 강제할 수 있다.

| 제어자    | 설명                                     |
| --------- | ---------------------------------------- |
| public    | 어디서나 접근 가능 (기본값)              |
| protected | 해당 클래스와 서브클래스에서만 접근 가능 |
| private   | 해당 클래스의 인스턴스에서만 접근 가능   |

## static

- 클래스의 속성과 메서드를 new 인스턴스화 하지 않고 호출할 수 있다
- 접근 제어자를 활용할 수 있다.
- 몇가지 정적 이름을 사용할 수 없다
  - 클래스는 그 자체로 new로 호출할 수 있는 함수이기 때문이다
  - ex) function.name

```ts
class StaticClass {
  private static type = "Type";

  static getType() {
    return StaticClass.type;
  }
}

// console.log(StaticClass.type)
console.log(StaticClass.getType());
```

## readonly

```ts
/**
 * readonly
 * - TypeScript에서만 제공
 */

class Person {
  name: string;
  readonly age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

const p = new Person("Jang", 99);

p.age = 30; // age는 readonly 이기 떄문에 수정이 불가능합니다.
console.log(p);
```

## 추상 클래스

- abstract를 선언한 클래스로 직접 인스턴스화 될 수 없는 클래스이다.
- 직접 인스턴스화 될 수 없지만 extends 후 파생된 클래스를 인서턴스화하도록 유도한다.
- 추상 클래스는 구현된 메서드를 포함시킬 수 있다.
- abstract 선언한 메서드는 파생된 클래스에서 메서드를 구현해야 한다.

```ts
abstract class Animal {
  // 선언된 메서드
  abstract hello(): string;

  // 구현된 메서드
  run() {
    return this.hello();
  }
}

// 직접 인스턴스가 될 수 없다.
// const animal = new Animal()

class Person extends Animal {
  hello() {
    return "Person";
  }
}

class Dog extends Animal {
  hello() {
    return "Person";
  }
}
const person = new Person();
const dog = new Dog();

console.log(person.hello());
```

## Parameter Properties

```ts
class Person {
  public name: string;
  private age: number;
  protected gender: "M" | "F";

  constructor(name: string, age: number, gender: "M" | "F") {
    this.name = name;
    this.age = age;
    this.gender = gender;
  }
}
```

- 중복되는 코드가 많아서 복잡합니다.
- 가독성이 떨어지긴 하지만 간단하게 바꿀 수 있습니다.

```ts
class Person {
  constructor(
    public name: string,
    private age: number,
    protected gender: "M" | "F"
  ) {}
}
```

## 인터페이스

- Js에서는 존재하지 않습니다
- 객체의 타입을 정의하고 생김새를 가지도록 할 수 있습니다.
- TS에서의 클래스 기능은 C#에서 유래된 것이 많습니다.
- 일부 기능은 TS에서만 존재하는 고유 문법으로 컴파일 후에 사라집니다.
- extends가 아닌 implements 키워드로 구현합니다.

```TS
interface Animal {
    name: string
    run(): void
}

interface Person {
    sayName(): string
}

class Jang implements Animal, Person {
    constructor(public name: string) {}

    run() {
        console.log(this.name)
    }

    sayName() {
        return `이름은 ${this.name}`
    }
}
```

- interface 에서의 extends

```TS
interface Animal {
    name: string
    run(): void
}

interface Person extends Animal {
    sayName(): string
}

const jang: Person = {
    name: 'Sono',
    run() {
        return 'string'
    },
    sayName() {
        return 'string2'
    }
}
```

## in, instanceof, is

```TS
/**
 * in
 * JS에서 객체가 특정 속성을 가지고 있는지 검사를 불리언으로 반환합니다.
 */

interface Dog {
    name: string
    bark(): '멍멍'
}
interface Cat {
    name: string
    meow(): '야옹'
}

function sayAnimal(animal: Dog | Cat) {
    if ('bark' in animal) {
        animal.bark()
        animal.name
    }
}

// instanceof
function getDate(date: Date | string): Date {
    if(date instanceof Date) {
        return date
    }

    return new Date(date)
}

// is
function isDog(animal:Dog | Cat): animal is Dog {
    return 'bark' in animal
}

interface Dog {
    name: string
    bark(): '멍멍'
}
interface Cat {
    name: string
    meow(): '야옹'
}

function sayAnimal(animal: Dog | Cat) {
    if (isDog(animal)) {
        animal.bark()
        animal.name
    }
}
```

---

## 열거형

- 의미있는 상수 자료를 정의할 수 있습니다(문서화)
- 키를 값에 할당하며 순서가 없는 집합이자 자료구조입니다.
- `enum`키워드 + `PascalCase` 조합으로 생성
- 계산된 값을 사용할 수 있습니다.
  - 타입스크립트가 알아서 추론

```TS
enum Prize {
    Gold = 100,
    Silver,
    Bronze
}

console.log(Prize)
```

### 문자형 열거

- 각 멤버의 값을 문자열로 초기화되어야 합니다.
- 숫자형 열거와 동장 방식이 다릅니다
  - 값이 자동으로 증가하지 않습니다
  - 이외에 리버스 매핑의 차이점도 존재합니다

### 혼합형 열거

- 지원은 하지만 비추천하는 열거형입니다.

```TS
enum BollLikeEnum {
    No = 0,
    Yes = 'Yes'
}
```

### const 열거

- 기본적으로 열거형은 불안전한 접근을 허용합니다
  - `const enum`은 이러한 점을 보완하기 위한 안전한 열거형
- `enum` 앞에 `const` 키워드를 명시합니다
- 컴파일 후 제거되기 때문에 JavaScript 코드를 생성하지 않습니다

### 열거형 활용

- 런타임에 존재하는 실제 객체
- `keyof`, `keyof typeof` 와 조합하여 활용할 수 있다.

```Ts
enum Language {
    TypeScript = "TS",
    JavaScript = 'JS',
    Java = 'JAVA',
    Ruby = 'RB',
}

type LangCode = keyof typeof Language
// 위와 아래가 같다
type LangCode2 = 'TypeScript' | 'JavaScript' | 'Java' | 'Ruby'

function getLang(langCode: LangCode) {
    console.log(langCode)
}
```

---

## 논리 연산자 활용 타입

- 타입 별칭 소개
  - 의미없는 반복을 줄이고 타입을 명시적으로 사용하도록 도와줍니다
  - `let`, `const` 를 선언해 변수를 초기화 하듯이 사용할 수 있습니다
  - 컴파일러가 따로 추론하지 않습니다

```ts
/**
 * Type Aliases(타입 별칭)
 */

type str = string;
type num = number;
type arr = num[];
type func = () => void;

type Person = {
  name: str;
  age: num;
  counts: arr;
  getInfo: func;
};

interface PersonInterface {
  name: str;
  age: num;
  counts: arr;
}
```

## Union 타입

```Ts
type StringOrNumber = string | number
type GenderType = 'M' | 'F'

const a:StringOrNumber = 'Str'
const b:StringOrNumber = 123

type Person = {
    name: string
    age: number
}

type Me = {
    name: string
    genderType: GenderType
}

const obj: Person | Me = {
    name: 'Sono',
    age: 27,
    genderType: 'M'
}
```

## VS 에서의 TS 빌드

`tsc src/파일이름.ts` 를 해주면 파일이름.js 가 나옵니다.

`tsc src/파일이름.ts --declaration` 를 해주면 파일이름.d.ts 가 나옵니다.
