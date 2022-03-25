# 화살표함수

- argument, this 조심
- ...nums와 같은 나머지 매개변수는 화살표함수에서도 사용 가능

# 객체

```js
// 싱글 리터럴 객체
const object = {
  property: "value",
  method: function () {},
};

// PascalCase, 생성자 함수
function NewObject(name) {
  this.name = name;
}

const newObject = new NewObject("name");

// const newObject2 = Object.create(프로토타입 , 객체 서술자(기술자));
const newObject2 = Object.create(Object.prototype, {
  name: {
    value: "jang",
    writeable: true, // 덮어쓸 수 있는지
    enumerable: true, // 열거할 수 있는지
    configurable: true, // 객체 서술자를 수정할 수 있는지
  },
});

console.log(newObject2);
```

## 프로퍼티

```js
// 프로퍼티 열거

const obj = {
  prop1: "value1",
  prop2: "value2",
  prop3: "value3",
  prop4: "value4",
};

for (const key in obj) {
  if (obj.hasOwnProperty(key)) {
    console.log(obj[key]);
  }
}

// 프로퍼티 조작

const person = {
  firstName: "jang",
  location: "korea",
};

person.lastName = "hyeonseok";

delete person.location;

console.log(person);

// 프로퍼티 접근자(getter, setter)

const person = {
  _firstName: "jang",
  location: "korea",

  get firstName() {
    return this._firstName;
  },

  set firstName(newFristName) {
    if (typeof newFristName !== "string") {
      this._firstName = "undefined name";

      return;
    }
    this._firstName = newFristName;
  },
};

console.log(person.firstName);
```

# 자료 다루기

## 객체를 배열로 순회하기

- Object.keys()
- Object.values(object1)
- Object.entries(object1) : [key, value] 쌍의 배열을 반환합니다.
- Array.prototype.concat() : 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환합니다.

## 배열 고차 함수

- map
- filter
- reduce : 누적된 값

```js
function sumTotal(...numbers) {
  return numbers.reduce(function (total, current) {
    return total + current;
  }, 0); // 초기값 total로 들어감
}

// 화살표 함수로 만들 시
function sumTotal(...numbers) {
  return numbers.reduce((total, current) => total + current, 0);
}
console.log(sumTotal(1, 2, 3, 4, 5));
```

- sort

```js
number.sort(function (a, b) {
  return a - b;
});

// 문자를 비교할 시
strings.sort(function (a, b) {
  return a.localeCompare(b);
});
```

# 호이스팅

- 변수 선언을 끌어 올린다.
- 호이스팅을 방지하기위해 var 대신 let, const 를 사용합니다.

# IIFE (Immediately Invoked Function Expression)

```js
(function () {
  var aName = "Barry";
})();
```

- let, const의 경우에는 상관없지만 var의 경우에는 다른곳에서도 var의 값을 참조하려하기에 IIFE를 사용한다.
- IIFE는 세미콜론을 앞이나 뒤에 꼭 붙여준다.

# JSON

- JSON -> "JS Object" (JSON Parse) => 서버에서 데이터를 가져올 때
- JS Object -> "JSON" (JSON stringfy) => 서버로 데이터를 보낼 때

# this 명시적 바인딩

```js
const zero = {
  name: "베이스",
  sayName: function () {
    return this.name + "입니다";
  },
};

function sayFullName(firstName) {
  return firstName + this.sayName();
}

const result = sayFullName.call(zero, "장"); // this 명시적 바인딩
console.log(result);

const result2 = sayFullName.apply(zero, ["제로", "Zero"]); // 인수를 배열로 받을땐 call이아닌 apply
console.log(result2);

const sayFullNameZero = sayFullName.bind(zero); // bind가 가장 편리
console.log(sayFullNameZero("제로"));
```

---

# 클래스

- 객체를 생성하기 위한 템플릿입니다.

```js
class Person {
  constructor(name, age, location) {
    this.name = name;
    this.age = age;
    this.location = location;
  }

  getName() {
    return this.name + "입니다";
  }
}

// 클래스 확장
class Friends extends Person {
  constructor(name, age, location) {
    super(name, age, location);
  }
}

const me = new Friends("chae", 10, "Korea");

console.log(me.getName());
```

---

# 클로저

- 사용 할 일 있을 때 다시 찾아보기

---

# 비동기와 동기

- 비동기 예제

```js
console.log("1");
setTimeout(() => {
  console.log("2");
}, 1000);
console.log("3");
// 1 > 3 > 2 순서로 실행된다.
```

## 콜백

```js
console.log("1");

function setTimeoutWithCallback(callbackFunc) {
  setTimeout(() => {
    console.log("2");
    callbakcFunc();
  }, 1000);
}
setTimeoutWithCallback(() => console.log("3"));
// 1 > 2 > 3 출력
```

---

## Promise

```js
const starbucks = function (coffeeName) {
  return new Promise((resolve, reject) => {
    if (coffeeName === "아메리카노") {
      resolve("아메리카노 한잔입니다");
    } else {
      reject("아메리카노는 없습니다.");
    }
  });
};

starbucks("아메리")
  .then((res) => console.log(res))
  .catch((rej) => console.log(rej))
  .finally(() => console.log("갑사합니다"));
```

---

## async, await

```js
async function americano(someDrink) {
  try {
    const result = await starbucks();

    return result;
  } catch (error) {
    console.log(error);
  } finally {
    console.log("감사합니다");
  }
}

console.log(americano("아메리카노"));
```

---

# 이벤트

## 이벤트 버블링

- 상위 요소로 전파된다.

```js
button.addEventListener("click", (event) => {
  event.stopPropagation(); // 설정하면 버블링이 일어나지 않는다

  window.alert("button");
});
```

## 이벤트 캡처링

- 상위에서 하위요소로 전파된다.

```js
button.addEventListener(
  "click",
  (event) => {
    event.stopPropagation(); // 설정하면 버블링이 일어나지 않는다

    window.alert("button");
  },
  true
); // 기본 값으로 captrue: false 가 되있다. false일 경우에는 버블링 ture로 바꿔줄 경우에는 캡처링이 발생한다.
```

## 이벤트 위임

```js
const items = document.querySelector("ul"); // ul에 이벤트를 달아두면 ul에 속해있는 li에도 이벤트가 다 발생한다.
```

## debounce

- 마지막 호출 이후 일정 밀리세컨드 이후로 지연된 호출을 하도록 만드는 함수
- 이벤트 발생이 많을 때 가장 마지막 이벤트만을 실행시킨다.

```js
function debounc(callback, wait) {
  let timeout;

  // 함수가 호출시 매번 반환
  return function (...args) {
    const context = this;

    // 타이머를 취소시켜준다.
    clearTimeout(timeout);
    timeout = setTimeout(() => callback.apply(context, args), wait);
  };
}
```

## throttle

- 이벤트 발생이 많을 때 특정 밀리세컨드 이벤트를 차단하고 단 한번만 실행시킨다
- 무한 스크롤할 경우에 사용하기 적절함
- 매개변수 : 실행시킬 함수, 차단시킬 밀리세컨드
- 보통 lodash에서 많이 사용함
- debounce throttle 구글링해서 잘 이해하기.

```js
function throttle(callback, wait) {
  let timeout = null;

  return function (...args) {
    const context = this;

    if (!timeout) {
      timeout = setTImeout(() => {
        callback, apply(this, args);
        timeout = null;
      }, wait);
    }
  };
}
```

## 이벤트 루프

- 비동기 방식으로 동시성을 지원하는 방법
- Javascript 엔진은 한 번에 한 개의 코드만 실행할 수 있다.
- 하지만 사용되는 환경은 동시에 많은 작업이 처리된다.

- 프로세스 : 프로그램을 메모리에 할당
- 스레드 : 프로세스 내의 실행 단위
- 스택 : Last In First Out
- 큐 : First In First out
