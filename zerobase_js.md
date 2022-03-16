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
