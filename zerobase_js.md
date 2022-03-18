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
