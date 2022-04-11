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

5. 두 수 최대 합
6. 일곱 난장이
7. Two Sum : for문 한개로 풀기
8. 달팽이 만들기

---

# 프로토타입

- 어떠한 객체가 만들어지기 위해 객체의 모태가 되는 원형
- 자바스크립트는 일반적인 객체지향 언어와는 다르게, 프로토타입을 이용한 복사를 통해 새로운 객체 생성
- 일반적인 객체 생성 방식: 속성은 생성자, 메서드는 프로토타입에서 정의

```js
// 생성자에서 속성 정의

function Test(a, b) {
  // 속성 정의
}

// 첫 메소드 정의
Test.prototype.x = function() { ... };

// 두번째 메소드 정의
Test.prototype.y = function() { ... };

// 객체 생성
let test = new Test(1, 2);
```

- 예제

```js
// 생성자 속성 정의
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// prototype을 이용한 Person 메서드 정의
Person.prototype.isAudult = function () {
  return this.age > 18;
};

// 객체 생성
const p1 = new Person("bob", 26);
const p2 = new Person("Alice", 16);

console.log(p1);
console.log(p2);

console.log(p1.isAudult());
```

---

# 연결리스트 (Linked List)

- 각 노드가 데이터와 포인터를 가지며, 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료 구조
- 구현 메서드(method)

  - 노드 개수 / 비어 있는지 확인 / 노드 출력: LinkedList.size(), LinkedList.isEmpty(), LinkedList.printNode()
  - 노드 추가 : LinkedList.append(), LinkedList.insert()
  - 노드 삭제 : LinkedList.remove(), LinkedList.removeAt()
  - 데이터 위치 확인 : LinkedList.indexOf()

- 사용 예시

```js
// Node(): data와 point를 가지고 있는 객체
function Node(data) {
  this.data = data;
  this.next = null;
}

// LinkedList(): head와 length를 가지고 있는 객체
function LinkedList() {
  this.head = null;
  this.length = 0;
}

// size() : 연결 리스트 내 노드 개수 확인
LinkedList.prototype.size = function () {
  return this.length;
};

// isEmpty() : 객체 내 노드 존재 여부 파악
LinkedList.prototype.isEmpty = function () {
  return this.length === 0;
};

// printNode() : 노드 출력
LinkedList.prototype.printNode = function () {
  for (let node = this.head; node != null; node = node.next) {
    process.stdout.write(`${node.data} -> `);
  }
  console.log("null");
};

// append() : 연결 리스트 가장 끝에 노드 추가
LinkedList.prototype.append = function (value) {
  let node = new Node(value);
  current = this.head;

  if (this.head === null) {
    this.head = node;
  } else {
    while (current.next != null) {
      current = current.next;
    }
    current.next = node;
  }

  this.length++;
};

// insert() : position 위치에 노드 추가
LinkedList.prototype.insert = function (value, position = 0) {
  if (position < 0 || position > this.length) {
    return false;
  }

  let node = new Node(value),
    current = this.head,
    index = 0,
    prev;
  if (position === 0) {
    node.next = current;
    this.head = node;
  } else {
    while (index++ < position) {
      prev = current;
      current = current.next;
    }

    node.next = current;
    prev.next = node;
  }

  this.length++;
};

// remove() : value 데이터를 찾아 노드 삭제
LinkedList.prototype.remove = function (value) {
  let current = this.head,
    prev = current;

  while (current.data != value && current.next != null) {
    prev = current;
    current = current.next;
  }

  if (current.data != value) {
    return null;
  }

  if (current === this.head) {
    this.head = current.next;
  } else {
    prev.next = current.next;
  }

  this.length--;

  return current.data;
};

// reoveAt(): position 위치 노드 삭제
LinkedList.prototype.removeAt = function (position = 0) {
  if (position < 0 || position >= this.length) {
    return null;
  }

  let current = this.head,
    index = 0,
    prev;

  if (position === 0) {
    this.head = current.next;
  } else {
    while (index++ < position) {
      prev = current;
      current = current.next;
    }

    prev.next = current.next;
  }

  this.length--;

  return current.data;
};

// indexOf() : value 값을 갖는 위치 반환
LinkedList.prototype.indexOf = function (value) {
  let current = this.head,
    index = 0;

  while (current != null) {
    if (current.data === value) {
      return index;
    }

    index++;
    current = current.next;
  }

  return -1;
};

// remove2() : indexOf + removeAt
LinkedList.prototype.remove2 = function (value) {
  let index = this.indexOf(value);
  return this.removeAt(index);
};

let ll = new LinkedList();
console.log(ll);

ll.insert(1);
ll.insert(10);
ll.insert(100);
ll.insert(2, 1);
ll.insert(3, 3);
ll.printNode();

console.log(ll.indexOf(1000));
console.log(ll.indexOf(1));
console.log(ll.indexOf(100));
console.log(ll.indexOf(10));

console.log(ll.remove2(1000));
ll.printNode();
console.log(ll.remove2(1));
ll.printNode();
console.log(ll.remove2(2));
ll.printNode();
console.log(ll.remove2(100));
ll.printNode();

console.log(ll.size());
```

---

# 이중 연결 리스트(Double Linked List)

```js
// Node(): data와 point인 next, prev를 가지고 있는 객체
function Node(data) {
  this.data = data;
  this.next = null;
  this.prev = null;
}

// DoubleLinkedList(): head, tail와 length를 가지고 있는 객체
function DoubleLinkedList() {
  this.head = null;
  this.tail = null;
  this.length = 0;
}

// size() : 연결 리스트 내 노드 개수 확인
DoubleLinkedList.prototype.size = function () {
  return this.length;
};

// isEmpty() : 객체 내 노드 존재 여부 파악
DoubleLinkedList.prototype.isEmpty = function () {
  return this.length === 0;
};

DoubleLinkedList.prototype.printNode = function () {
  process.stdout.write(`head -> `);
  for (let node = this.head; node != null; node = node.next) {
    process.stdout.write(`${node.data} -> `);
  }
  console.log("null");
};

DoubleLinkedList.prototype.printNodeInverse = function () {
  let temp = [];

  process.stdout.write("null <- ");
  for (let node = this.tail; node != null; node = node.prev) {
    temp.push(node.data);
  }
  for (let i = temp.length - 1; i >= 0; i--) {
    process.stdout.write(`${temp[i]} <- `);
  }
  console.log("tail");
};

DoubleLinkedList.prototype.append = function (value) {
  let node = new Node(value);

  if (this.head === null) {
    this.head = node;
    this.tail = node;
  } else {
    // DoubleLinkedList는 tail이 있기에 LinkedList와는 달리 while문이 필요 없다.
    this.tail.next = node;
    node.prev = this.tail;
    this.tail = node;
  }

  this.length++;
};

DoubleLinkedList.prototype.insert = function (value, position = 0) {
  if (position < 0 || position > this.length) {
    return false;
  }

  let node = new Node(value),
    current = this.head,
    index = 0,
    prev;

  if (position === 0) {
    if (this.head === null) {
      this.head = node;
      this.tail = node;
    } else {
      node.next = current;
      current.prev = node;
      this.head = node;
    }
  } else if (position === this.length) {
    current = this.tail;
    current.next = node;
    node.prev = current;
    this.tail = node;
  } else {
    while (index++ < position) {
      prev = current;
      current = current.next;
    }

    node.next = current;
    prev.next = node;

    current.prev = node;
    node.prev = prev;
  }

  this.length++;

  return true;
};

DoubleLinkedList.prototype.remove = function (value) {
  let current = this.head,
    prev = current;

  while (current.data != value && current.next != null) {
    prev = current;
    current = current.next;
  }

  if (current.data != value) {
    return null;
  }

  if (current === this.head) {
    this.head = current.next;
    if (this.length === 1) this.tail = null;
    else this.head.prev = null;
  } else if (current === this.tail) {
    this.tail = current.prev;
    this.tail.next = null;
  } else {
    prev.next = current.next;
    current.next.prev = prev;
  }

  this.length--;
  return current.data;
};

DoubleLinkedList.prototype.removeAt = function (position = 0) {
  if (position < 0 || position >= this.length) {
    return null;
  }

  let current = this.head,
    index = 0,
    prev;

  if (position === 0) {
    this.head = current.next;
    if (this.length === 1) this.tail = null;
    else this.head.prev = null;
  } else if (position === this.length - 1) {
    current = this.tail;
    this.tail = current.prev;
    this.tail.next = null;
  } else {
    while (index++ < position) {
      prev = current;
      current = current.next;
    }

    prev.next = current.next;
    current.next.prev = prev;
  }

  this.length--;

  return current.data;
};

// indexOf() : value 값을 갖는 위치 반환
DoubleLinkedList.prototype.indexOf = function (value) {
  let current = this.head,
    index = 0;

  while (current != null) {
    if (current.data === value) {
      return index;
    }

    index++;
    current = current.next;
  }

  return -1;
};

// remove2() : indexOf + removeAt
DoubleLinkedList.prototype.remove2 = function (value) {
  let index = this.indexOf(value);
  return this.removeAt(index);
};

let dll = new DoubleLinkedList();

dll.insert(1);
dll.insert(10);
dll.insert(100);
dll.insert(2, 1);
dll.insert(3, 3);
dll.printNode();
dll.printNodeInverse();

console.log(dll.removeAt(1000));
dll.printNode();
dll.printNodeInverse();
console.log(dll.removeAt(4));
dll.printNode();
dll.printNodeInverse();
console.log(dll.removeAt());
dll.printNode();
dll.printNodeInverse();
console.log(dll.removeAt(1));
dll.printNode();
dll.printNodeInverse();
```

---

# 원형 연결 리스트 (Circular Linked List)

```js
function Node(data) {
  this.data = data;
  this.next = null;
}

function CircularLinkedList() {
  this.head = null;
  this.length = 0;
}

CircularLinkedList.prototype.size = function () {
  return this.length;
};

CircularLinkedList.prototype.isEmpty = function () {
  return this.length === 0;
};

CircularLinkedList.prototype.printNode = function () {
  process.stdout.write("head -> ");

  if (this.length != 0) {
    process.stdout.write(`${this.head.data} -> `);
    for (let node = this.head.next; node != this.head; node = node.next) {
      process.stdout.write(`${node.data} -> `);
    }
  }

  console.log("head");
};

CircularLinkedList.prototype.insert = function (value, position = 0) {
  if (position < 0 || position > this.length) {
    return false;
  }

  let node = new Node(value),
    current = this.head,
    index = 0,
    prev;

  if (position === 0) {
    node.next = current;

    if (this.isEmpty()) {
      current = node;
    } else {
      while (current.next != this.head) {
        current = current.next;
      }
    }
    this.head = node;
    current.next = this.head;
  } else {
    while (index++ < position) {
      prev = current;
      current = current.next;
    }

    node.next = current;
    prev.next = node;

    if (node.next === null) {
      node.next = this.head;
    }
  }

  this.length++;

  return true;
};

CircularLinkedList.prototype.append = function (value) {
  let node = new Node(value),
    current = this.head;

  if (this.head === null) {
    this.head = node;
  } else {
    while (current.next != this.head) {
      current = current.next;
    }
    current.next = node;
  }

  node.next = this.head;

  this.length++;
};

CircularLinkedList.prototype.remove = function (value) {
  let current = this.head,
    prev,
    data;

  while (current.data != value && current.next != this.head) {
    prev = current;
    current = current.next;
  }

  if (current.data != value) {
    return null;
  }

  data = current.data;
  if (current === this.head) {
    while (current.next != this.head) {
      current = current.next;
    }

    this.head = this.head.next;
    current.next = this.head;
  } else {
    prev.next = current.next;
  }

  this.length--;

  return data;
};

CircularLinkedList.prototype.removeAt = function (position = 0) {
  if (position < 0 || position >= this.length) {
    return null;
  }

  let current = this.head,
    index = 9,
    prev,
    data;

  if (position === 0) {
    data = current.data;

    while (current.next != this.head) {
      current = current.next;
    }

    this.head = this.head.next;
    current.next = this.head;
  } else {
    while (index++ < position) {
      prev = current;
      current = current.next;
    }

    data = current.data;
    prev.next = current.next;
  }

  this.length--;

  return data;
};

let cll = new CircularLinkedList();

cll.insert(1);
cll.insert(10);
cll.insert(100);
cll.insert(2, 1);
cll.insert(3, 3);

console.log(cll.remove(1000));
cll.printNode();
console.log(cll.remove(1));
cll.printNode();
console.log(cll.remove(2));
cll.printNode();
console.log(cll.remove(100));
cll.printNode();

console.log(cll.size());
```

## 연결리스트 문제 전부 다시 풀어보기

---

# 스택(Stack)

- 나중에 넣은 데이터가 먼저 나오는 LIFO 기반의 선형 자료 구죠
- 구현 메서드(method)
  - 데이터 전체 획득 / 비어 있는지 확인: Stack.getBuffer(), Stack.isEmpty()
  - 추가 / 삭제 / 마지막 데이터 조회 / 크기 확인 : Stack.push(), Stack.pop(), Stack.peak(), Stack.size()
  - 데이터 위치 / 존재 여부 확인 : Stack.indexOf(), Stack.includes()

```js
// Stack(): 생성자 함수
function Stack(array) {
  this.array = array ? array : [];
}

// getBuffer(): 객체 내 데이터 셋 반환
Stack.prototype.getBuffer = function () {
  return this.array.slice();
};

// isEmpty(): 객체 내 데이터 O/X
Stack.prototype.isEmpty = function () {
  return this.array.length === 0;
};

// push(): 데이터 추가
Stack.prototype.push = function (element) {
  return this.array.push(element);
};

// pop(): 데이터 삭제
Stack.prototype.pop = function () {
  return this.array.pop();
};

// peek(): 가장 끝 데이터 반환
Stack.prototype.peek = function () {
  return this.array[this.array.length - 1];
};

// size(): 스택 내 데이터 개수 확인
Stack.prototype.size = function () {
  return this.array.length;
};

// indexOf(); 매개변수로 넘어온 element 위치 확인
Stack.prototype.indexOf = function (element, position = 0) {
  // return this.array.indexOf(element, position);
  for (let i = position; i < this.array.length; i++) {
    if (element === this.array[i]) return i;
  }
  return -1;
};

// includes(): 데이터 존재 여부 확인
Stack.prototype.includes = function (element, position = 0) {
  // return this.array.includes(element);
  for (let i = position; i < this.array.length; i++) {
    if (element === this.array[i]) return true;
  }
  return false;
};

let stack = new Stack([1, 2, 3]);

console.log(stack.indexOf(1));
console.log(stack.indexOf(1, 2));
console.log(stack.includes(1));
console.log(stack.includes(5));
```

## 스택 문제 다시 풀어보기

---

# 큐

- 먼저 넣은 데이터가 먼저 나오는 FIFO 기반의 선형 자료 구조
  - 데이터 추가 / 삭제: Queue.enqueue(), Queue.dequeue()

```js
// Queue() : 생성자 함수로 초기 데이터 설정
function Queue(array) {
  this.array = array ? array : [];
}

// getBuffer()
Queue.prototype.getBuffer = function () {
  return this.array.slice();
};

// isEmpty()
Queue.prototype.isEmpty = function () {
  return this.array.length === 0;
};

// enqueue()
Queue.prototype.enqueue = function (element) {
  return this.array.push(element);
};

// dequeue()
Queue.prototype.dequeue = function () {
  return this.array.shift();
};

// front()
Queue.prototype.front = function () {
  return this.array.length === 0 ? undefined : this.array[0];
};

// size()
Queue.prototype.size = function () {
  return this.array.length;
};

// clear()
Queue.prototype.clear = function () {
  this.array = [];
};

let queue = new Queue([1, 2]);

console.log(queue);

queue.enqueue(3);
queue.enqueue(4);
console.log(queue);

console.log(queue.dequeue());
console.log(queue.dequeue());
console.log(queue);
```

shift 는 시간이 오래걸리기에 enqueue, dequeue는 다음과 같이 만든다.

```js
// Queue() : 생성자 함수로 초기 데이터 설정
function Queue(array) {
  this.array = array ? array : [];
  this.tail = array ? array.length : 0;
  this.head = 0;
}

// getBuffer()
Queue.prototype.getBuffer = function () {
  return this.array.slice();
};

// isEmpty()
Queue.prototype.isEmpty = function () {
  return this.array.length === 0;
};

// enqueue()
Queue.prototype.enqueue = function (element) {
  return (this.array[this.tail++] = element);
};

// dequeue()
Queue.prototype.dequeue = function () {
  if (this.tail === this.head) return undefined;

  let element = this.array[this.head];
  delete this.array[this.head++];

  return element;
};

// front()
Queue.prototype.front = function () {
  return this.array.length === 0 ? undefined : this.array[0];
};

// size()
Queue.prototype.size = function () {
  return this.array.length;
};

// clear()
Queue.prototype.clear = function () {
  this.array = [];
};

let queue = new Queue([1, 2]);

console.log(queue);

queue.enqueue(3);
queue.enqueue(4);
console.log(queue);

console.log(queue.dequeue());
console.log(queue.dequeue());
console.log(queue);
```

## 우선순위 큐

- 우선순위를 고려하여 먼저 넣은 데이터가 먼저 나오는 FIFO 기반의 선형 자료 구조
- 우선순위 정렬 방식: 배열 기반, 연결리스트 기반, 힙(Heap) 기반 등의 정렬 방식 존재
- 구현 메서드

```js
// Element() : 데이터와 우선순위를 저장하기 위한 생성자 함수
function Element(data, priority) {
  this.data = data;
  this.priority = priority;
}

// PriorityQueue() : Element 관리를 위한 생성자 함수
function PriorityQueue() {
  this.array = [];
}

// getBuffer(): 객체 내 데이터 셋 반환
PriorityQueue.prototype.getBuffer = function () {
  return this.array.map((element) => element.data);
};

// isEmpty()
PriorityQueue.prototype.isEmpty = function () {
  return this.array.length === 0;
};

// enqueue()
PriorityQueue.prototype.enqueue = function (data, priority) {
  let element = new Element(data, priority);
  let added = false;

  for (let i = 0; i < this.array.length; i++) {
    if (element.priority < this.array[i].priority) {
      this.array.splice(i, 0, element);
      added = true;
      break;
    }
  }

  if (!added) {
    this.array.push(element);
  }

  return this.array.length;
};

// dequeue()
PriorityQueue.prototype.dequeue = function () {
  return this.array.shift();
};

let pq = new PriorityQueue();

pq.enqueue("Alice", 1);
pq.enqueue("Bob", 2);
console.log(pq);
pq.enqueue("Sono", 1);
console.log(pq);
```

---

# 원형 큐(Circular Queue)

- 원형 형태를 가지며, 먼저 넣은 데이터가 먼저 나오는 FIFO 기반의 선형 자료 구조

```js
const DEFAULT_SIZE = 5;

// CircularQueue() : 초기 속성값 설정을 위한 생성자 함수
function CircularQueue(array = [], size = DEFAULT_SIZE) {
  this.array = array;
  this.size = array.length > size ? array.length : size;
  this.length = array.length;
  this.head = 0;
  this.tail = array.length;
}

// getBuffer() : 객체 내 데이터 셋 반환
CircularQueue.prototype.getBuffer = function () {
  return this.array.slice();
};

// isEmpty()
CircularQueue.prototype.isEmpty = function () {
  return this.length === 0;
};

// isFull()
CircularQueue.prototype.isFull = function () {
  return this.length == this.size;
};

CircularQueue.prototype.enqueue = function (element) {
  if (this.isFull()) return false;

  this.array[this.tail % this.size] = element;
  this.tail = (this.tail + 1) % this.size;
  this.length++;

  return true;
};

CircularQueue.prototype.dequeue = function () {
  if (this.isEmpty()) return undefined;

  let element = this.array[this.head % this.size];
  delete this.array[this.head % this.size];
  this.head = (this.head + 1) % this.size;
  this.length--;

  return element;
};

CircularQueue.prototype.front = function () {
  return this.length === 0 ? undefined : this.array[this.head];
};

CircularQueue.prototype.dataSize = function () {
  return this.length;
};

CircularQueue.prototype.clear = function (size = DEFAULT_SIZE) {
  this.array = [];
  this.size = size;
  this.length = 0;
  this.head = 0;
  this.tail = 0;
};

let cq = new CircularQueue([1, 2, 3, 4]);

cq.enqueue(5);
cq.enqueue(6);
console.log(cq);

console.log(cq.dequeue());
console.log(cq.dequeue());
console.log(cq);

cq.enqueue(6);
console.log(cq);

cq.enqueue(8);
console.log(cq);
```

---

# 데크 (Deque)

- Double-Ended Queue 약자로, 삽입과 삭제가 양쪽 끝에서 모두 발생할 수 있는 선형 자료 구조

```js
// Deque()
function Deque(array = []) {
  this.array = array;
}

// getBuffer()
Deque.prototype.getBuffer = function () {
  return this.array.slice();
};

// isEmpty()
Deque.prototype.isEmpty = function () {
  return this.array.length === 0;
};

// pushFront()
Deque.prototype.pushFront = function (element) {
  return this.array.unshift(element);
};

// popFront()
Deque.prototype.popFront = function (element) {
  return this.array.shift(element);
};

// push()
Deque.prototype.pushBack = function (element) {
  return this.array.push(element);
};

// pop()
Deque.prototype.popBack = function (element) {
  return this.array.pop(element);
};

// front()
Deque.prototype.front = function () {
  return this.array.length === 0 ? undefined : this.array[0];
};

// back()
Deque.prototype.back = function () {
  return this.array.length === 0
    ? undefined
    : this.array[this.array.length - 1];
};

// size()
Deque.prototype.size = function () {
  return this.array.length;
};

// clear()
Deque.prototype.clear = function () {
  this.array = [];
};

let dq = new Deque([1, 2, 3]);
console.log(dq);

dq.pushFront(0);
dq.pushBack(4);
console.log(dq);
```

---

# 딕셔너리

```js
function Dictionary(items = {}) {
  this.items = items;
}

Dictionary.prototype.getBuffer = function () {
  return { ...this.items };
};

Dictionary.prototype.clear = function () {
  this.items = {};
};

Dictionary.prototype.size = function () {
  return Object.keys(this.items).length;
};

Dictionary.prototype.has = function (key) {
  return this.items.hasOwnProperty(key);
};

Dictionary.prototype.set = function (key, value) {
  this.items[key] = value;
};

Dictionary.prototype.get = function (key) {
  return this.has(key) ? this.items[key] : undefined;
};

Dictionary.prototype.remove = function (key) {
  if (this.has(key)) {
    delete this.item[key];
    return true;
  }

  return false;
};

Dictionary.prototype.keys = function () {
  return Object.keys(this.items);
};

Dictionary.prototype.values = function () {
  return Object.values(this.items);
};

Dictionary.prototype.each = function (fn) {
  for (let k in this.items) {
    fn(k, this.items[k]);
  }
};

function printDictionary(key, value) {
  console.log(`key: ${key}`);
  console.log(`vlaue: ${value}`);
}

let dict = new Dictionary();

dict.set("age", 19);
dict.set("name", "alice");

dict.each(printDictionary);
```

---

# 해시테이블

- 해시함수

  - 임의의 길이의 데이터를 고정된 길이의 데이터로 매핑하는 함수
  - 해시 함수 특성
    - 압축성 : 다양한 가변 길이의 입력에 대해 고정된 크기의 결과값을 반환하는 성질
    - 효율성 : 어떤 입력 값에 대해서도 많은 자원과 시간이 소요되지 않고 처리되는 성질
    - 저항성 : 결과값을 바탕으로 입력 값을 찾는 것이 불가능한 성질

- 해시테이블
  - Hash 함수를 사용하여 평균 O(1) 시간 복잡도로 특정 값을 신속하게 찾는 자료구조
  - 충돌 해결 방법
    - 해시 함수 변경 : 더 큰 숫자의 공간과 Modular 산술 값을 이용해 충돌 최소화
    - 자료구조 확장 : Open Addressing Method (선형 조사법, 이중해시), Close Addressing Method(체이닝)
  - 구현 메서드
    - 객체 초기화 / 크기 반환 : HashTable,clear(), HashTable,size()
    - 전체 데이터 반환, 전체 데이터 출력 : HashTable.getBuffer(), HashTable.print()
    - 데이터 추가 / 삭제 / 반환 : HashTable.put(), HashTable.remvoe(), HashTable.get()

## 해시테이블 충돌 및 해결

```js
const HASH_SIZE = 1013;

// Element() : key, value 저장을 위한 생성자

function Element(key, value) {
  this.key = key;
  this.value = value;
}

function HashTable() {
  this.table = new Array(HASH_SIZE);
  this.length = 0;
}

HashTable.prototype.hashCode = function (key) {
  // 이렇게 설정 함으로 써 충돌을 막아준다
  let hash = 5381;
  for (let i = 0; i < key.length; i++) {
    hash = hash * 33 + key.charCodeAt(i);
  }
  return hash % HASH_SIZE;
};

HashTable.prototype.put = function (key, value) {
  let index = this.hashCode(key);
  console.log(`key: ${key} -> index: ${index}`);

  if (this.table[index] !== undefined) {
    return false;
  }

  this.table[index] = new Element(key, value);
  this.length++;

  return true;
};

HashTable.prototype.get = function (key) {
  return this.table[this.hashCode(key)];
};

HashTable.prototype.remove = function (key) {
  let element = this.table[this.hashCode(key)];

  if (element !== undefined) {
    delete this.table[this.hashCode(key)];
    this.length--;
  }

  return element;
};

HashTable.prototype.clear = function () {
  this.table = new Array(HASH_SIZE);
  this.length = 0;
};

HashTable.prototype.size = function () {
  return this.length;
};

HashTable.prototype.getBuffer = function () {
  let array = [];
  for (let i = 0; i < this.table.length; i++) {
    if (this.table[i]) {
      array.push(this.table[i]);
    }
  }

  return array;
};

HashTable.prototype.print = function () {
  for (let i = 0; i < this.table.length; i++) {
    if (this.table[i]) {
      console.log(`${i} -> ${this.table[i].key} : ${this.table[i].value}`);
    }
  }
};

let ht = new HashTable();

ht.put("Ana", 172);
ht.put("Donnie", 183);
ht.put("Sue", 163);
ht.put("Jamie", 168);
ht.put("Paul", 190);

ht.print();
console.log(ht.getBuffer());

console.log(ht.size());
ht.clear();
console.log(ht);
```

## 선형 조사법 해시테이블

- Hash 충돌이 발생했을 때, 그 다음 주소를 확인하고 비어 있다면 그 자리에 대신 저장하는 자료구조

```js
const HASH_SIZE = 5;

// Element() : key, value 저장을 위한 생성자

function Element(key, value) {
  this.key = key;
  this.value = value;
}

function LinearHashTable() {
  this.table = new Array(HASH_SIZE);
  this.length = 0;
}

LinearHashTable.prototype.hashCode = function (key) {
  let hash = 0;
  for (let i = 0; i < key.length; i++) {
    hash += key.charCodeAt(i);
  }
  return hash % HASH_SIZE;
};

LinearHashTable.prototype.put = function (key, value) {
  let index = this.hashCode(key);
  let startIndex = index;
  console.log(`key: ${key} -> index: ${index}`);

  do {
    if (this.table[index] === undefined) {
      this.table[index] = new Element(key, value);
      this.length++;

      return true;
    }

    index = (index + 1) % HASH_SIZE;
  } while (index !== startIndex);

  return false;
};

LinearHashTable.prototype.get = function (key) {
  let index = this.hashCode(key);
  let startIndex = index;

  do {
    if (this.table[index] !== undefined && this.table[index].key === key) {
      return this.table[index].value;
    }

    index = (index + 1) % HASH_SIZE;
  } while (index !== startIndex);

  return undefined;
};

LinearHashTable.prototype.remove = function (key) {
  let index = this.hashCode(key);
  let startIndex = index;

  do {
    if (this.table[index] !== undefined && this.table[index].key === key) {
      let element = this.table[index];
      delete this.table[index];
      this.length--;

      return element;
    }

    index = (index + 1) % HASH_SIZE;
  } while (index !== startIndex);

  return undefined;
};

LinearHashTable.prototype.clear = function () {
  this.table = new Array(HASH_SIZE);
  this.length = 0;
};

LinearHashTable.prototype.size = function () {
  return this.length;
};

LinearHashTable.prototype.getBuffer = function () {
  let array = [];
  for (let i = 0; i < this.table.length; i++) {
    if (this.table[i]) {
      array.push(this.table[i]);
    }
  }

  return array;
};

LinearHashTable.prototype.print = function () {
  for (let i = 0; i < this.table.length; i++) {
    if (this.table[i]) {
      console.log(`${i} -> ${this.table[i].key} : ${this.table[i].value}`);
    }
  }
};

let lt = new LinearHashTable();

lt.put("Ana", 172);
lt.put("John", 179);
lt.put("Donnie", 182);
lt.put("Mindy", 142);
console.log(lt.put("Paul", 168));
console.log(lt.put("Sue", 163));

console.log(lt.remove("Donnie"));
console.log(lt);
```

## 체이닝 해시테이블

- 별도의 자료구조인 연결 리스트를 병합 사용하여 Hash 충돌을 해결한 해시테이블 기반 자료구조

```js

```

---

# 트리

- 두 노드 사이의 하나의 간선만 연결되어 있는, 최소 연결과 계층형태의 비선형 자료 구조

## 전위 순회 (Pre-order)

- N - L - R

```js
// 의사 코드 (pseudo-code)
preorder(node)
  print node.value
  if node.left !== null then preorder(node.left)
  if node.right !== null then preorder(node.right)
```

## 중위 순회 (In-order)

- L - N - R

```js
// 의사 코드 (pseudo-code)
inorder(node)
  print node.value
  if node.left !== null then inorder(node.left)
  print node.value
  if node.right !== null then inorder(node.right)
```

## 층별 순회 (Level-order) BFS에서 쓰임

1. root 노드 방문
2. Level 증가
3. 왼쪽에서 오른쪽 순으로 방문

```js
// 의사 코드 (pseudo-code)
levelorder(root)
  q.enqueue(root)
  whiel not q.empty do
    node := q.dequeue()
    print node.value
    if node.left !== null q.enqueue(node.left)
    if node.right !== null q.enqueue(node.right)
```

## 후위 순회 (Post-order)

- L - R - N

```js
// 의사 코드 (pseudo-code)
postorder(node)
  if node.left !== null then postorder(node.left)
  if node.right !== null then postorder(node.right)
  print node.value
```

## 이진 트리 (Binary Tree)

- 각각의 노드가 최대 두개의 자식 노드를 가지는 트리 자료 구조
- 활용방식

  - 검색과 정렬: 이진 탐색 트리와 이진 힙 구현에 활용
  - 허프만 코딩: 연관 분기 구조 위한 데이터 표현에 활용

- 이진트리의 종류

1. 포화 이진 트리(Perfect binary tree

- 모든 레벨의 노드가 가득 채워져 있는 트리
- leaf 노드를 제외한 모든 자식은 2개의 노드를 보유
- 노드의 개수 : 2^h - 1

2. 완전 이진 트리 (Complete binary tree)

- 마지막 레벨 전까지 노드가 가득 채워져 있고, 마지막 레벨은 왼쪽부터 순차적으로 채워져 있는 트리
- 배열을 사용해 효율적인 표현이 가능
- 노드의 개수 : n < 2^h - 1

3. 정 이진 트리 (Full binary tree)

- 모든 노드가 0개 또는 2개의 자식 노드만 갖는 트리
- proper 또는 plane 이진 트리라고도 불림
- 노드의 개수 : n < 2^h - 1

4. 편향 이진 트리 (Skewed binary tree)

- 왼쪽 혹은 오른쪽으로 편향되게 치우쳐 있는 트리
- 각각의 높이에 하나의 노드만 존재
- 노드의 개수 h

5. 균형 이진 트리 (Balanced binary tree)

- 삽입/삭제가 이루어 질 때, 왼쪽 서브 트리와 오른쪽 서브 트리의 높이 차를 1 이하로 맞추는 이진 탐색 트리

## 이진 트리 순회 (Binary Tree Traversal)

- 각각의 노드가 최대 두개의 자식 노드를 가지는 트리 자료 구조를 순회하는 방법

```js
/* Queue 객체 추가 */
function Queue(array) {
  this.array = array ? array : [];
}

Queue.prototype.isEmpty = function () {
  return this.array.length === 0;
};

Queue.prototype.enqueue = function (element) {
  return this.array.push(element);
};

Queue.prototype.dequeue = function () {
  return this.array.shift();
};

// Node(): value와 left, right node 저장을 위한 생성자
function Node(value) {
  this.value = value;
  this.left = null;
  this.right = null;
}

// BinaryTree(): 시작 노드인 root를 저장하기 위한 생성자
function BinaryTree() {
  this.root = null;
}

// _insertNode(): 재귀로 트리를 순회하며 노드 추가 (내부 사용)
BinaryTree.prototype._insertNode = function (node, value) {
  if (node === null) {
    node = new Node(value);
  } else if (value < node.value) {
    node.left = this._insertNode(node.left, value);
  } else if (value > node.value) {
    node.right = this._insertNode(node.right, value);
  }

  return node;
};

// insert(): 노드 추가
BinaryTree.prototype.insert = function (value) {
  this.root = this._insertNode(this.root, value);
};

// _preOrderTraverseNode(): 재귀로 트리를 순회하며 전위 순회 (내부 사용)
BinaryTree.prototype._preOrderTraverseNode = function (node, callback) {
  if (node === null) {
    return;
  }

  callback(node);
  this._preOrderTraverseNode(node.left, callback);
  this._preOrderTraverseNode(node.right, callback);
};

// preOrderTraverse(): 전위 순회하며 노드 출력
BinaryTree.prototype.preOrderTraverse = function (callback) {
  this._preOrderTraverseNode(this.root, callback);
};

// _inOrderTraverseNode(): 재귀로 트리를 순회하며 중위 순회 (내부 사용)
BinaryTree.prototype._inOrderTraverseNode = function (node, callback) {
  if (node === null) {
    return;
  }

  this._inOrderTraverseNode(node.left, callback);
  callback(node);
  this._inOrderTraverseNode(node.right, callback);
};

// inOrderTraverse(): 중위 순회하며 노드 출력
BinaryTree.prototype.inOrderTraverse = function (callback) {
  this._inOrderTraverseNode(this.root, callback);
};

// _postOrderTraverseNode(): 재귀로 트리를 순회하며 후위 순회 (내부 사용)
BinaryTree.prototype._postOrderTraverseNode = function (node, callback) {
  if (node === null) {
    return;
  }

  this._postOrderTraverseNode(node.left, callback);
  this._postOrderTraverseNode(node.right, callback);
  callback(node);
};

// postOrderTraverse(): 후위 순회하며 노드 출력
BinaryTree.prototype.postOrderTraverse = function (callback) {
  this._postOrderTraverseNode(this.root, callback);
};

// levelOrderTraverse(): 층별 순회하며 노드 출력
BinaryTree.prototype.levelOrderTraverse = function (callback) {
  let q = new Queue();
  let node;

  q.enqueue(this.root);
  while (!q.isEmpty()) {
    node = q.dequeue();
    callback(node);
    if (node.left !== null) q.enqueue(node.left);
    if (node.right !== null) q.enqueue(node.right);
  }
};

let tree = new BinaryTree();

tree.insert("F");
tree.insert("B");
tree.insert("A");
tree.insert("D");
tree.insert("C");
tree.insert("E");
tree.insert("G");
tree.insert("I");
tree.insert("H");

function printNode(node) {
  process.stdout.write(`${node.value} -> `);
}

console.log("********** Pre-Order **********");
tree.preOrderTraverse(printNode);
console.log("end");

console.log("********** In-Order **********");
tree.inOrderTraverse(printNode);
console.log("end");

console.log("********** Post-Order **********");
tree.postOrderTraverse(printNode);
console.log("end");

console.log("********** Level-Order **********");
tree.levelOrderTraverse(printNode);
console.log("end");
```

## 이진 탐색 트리

- 현재 노드를 기준으로 왼쪽에는 작은 값, 오른쪽은 큰 값으로 정렬해 놓는 이진 트리 기반 자료 구조

```js
// Node(): value와 left, right node 저장을 위한 생성자
function Node(value) {
  this.value = value;
  this.left = null;
  this.right = null;
}

// BinarySearchTree(): 시작 노드인 root를 저장하기 위한 생성자
function BinarySearchTree() {
  this.root = null;
}

// _inOrderTraverseNode(): 재귀로 트리를 순회하며 중위 순회 (내부 사용)
BinarySearchTree.prototype._inOrderTraverseNode = function (node, callback) {
  if (node === null) {
    return;
  }

  this._inOrderTraverseNode(node.left, callback);
  callback(node);
  this._inOrderTraverseNode(node.right, callback);
};

// inOrderTraverse(): 중위 순회하며 노드 출력
BinarySearchTree.prototype.inOrderTraverse = function (callback) {
  this._inOrderTraverseNode(this.root, callback);
  console.log("end");
};

// _insertNode(): 재귀로 트리를 순회하며 노드 추가 (내부 사용)
BinarySearchTree.prototype._insertNode = function (node, value) {
  if (node === null) {
    node = new Node(value);
  } else if (value < node.value) {
    node.left = this._insertNode(node.left, value);
  } else if (value > node.value) {
    node.right = this._insertNode(node.right, value);
  }

  return node;
};

// insert(): 노드 추가
BinarySearchTree.prototype.insert = function (value) {
  this.root = this._insertNode(this.root, value);
};

// _minNode(): 반복문으로 트리를 순회하며 최솟값 노드 탐색
BinarySearchTree.prototype._minNode = function (node) {
  if (node === null) {
    return null;
  }

  while (node && node.left !== null) {
    node = node.left;
  }

  return node.value;
};

// _maxNode(): 반복문으로 트리를 순회하며 최대값 노드 탐색
BinarySearchTree.prototype._maxNode = function (node) {
  if (node === null) {
    return null;
  }

  while (node && node.right !== null) {
    node = node.right;
  }

  return node.value;
};

// min(): 최솟값 노드 탐색
BinarySearchTree.prototype.min = function () {
  return this._minNode(this.root);
};

// max(): 최댓값 노드 탐색
BinarySearchTree.prototype.max = function () {
  return this._maxNode(this.root);
};

// _searchNode(): 재귀로 트리를 순회하며 값을 만족하는 노드 탐색
BinarySearchTree.prototype._searchNode = function (node, value) {
  if (node === null) {
    return false;
  }

  if (node.value === value) {
    return true;
  } else if (node.value > value) {
    return this._searchNode(node.left, value);
  } else if (node.value < value) {
    return this._searchNode(node.right, value);
  }
};

// search(): value 노드 탐색
BinarySearchTree.prototype.search = function (value) {
  return this._searchNode(this.root, value);
};

// _findMimNode(): 반복문으로 트리를 순회하며 최솟값을 보유한 노드 탐색/반환
BinarySearchTree.prototype._findMinNode = function (node) {
  while (node && node.left !== null) {
    node = node.left;
  }

  return node;
};

// _removeNode(): 재귀로 트리를 순회하며 값을 만족하는 노드를 찾고 삭제
BinarySearchTree.prototype._removeNode = function (node, value) {
  if (node === null) {
    return null;
  }

  if (node.value === value) {
    // case 1: 0 child node (leaf node)
    if (node.left === null && node.right === null) {
      node = null;
    }
    // case 2: 1 child node
    else if (node.left === null) {
      node = node.right;
    } else if (node.right === null) {
      node = node.left;
    }

    // case 3: 2 child node
    else {
      let aux = this._findMinNode(node.right);
      node.value = aux.value;
      node.right = this._removeNode(node.right, aux.value);
    }
  } else if (node.value > value) {
    node.left = this._removeNode(node.left, value);
  } else if (node.value < value) {
    node.right = this._removeNode(node.right, value);
  }

  return node;
};

// remove(): 노트 삭제
BinarySearchTree.prototype.remove = function (value) {
  this.root = this._removeNode(this.root, value);
};

let tree = new BinarySearchTree();

tree.insert("F");
tree.insert("B");
tree.insert("A");
tree.insert("D");
tree.insert("C");
tree.insert("E");
tree.insert("G");
tree.insert("I");
tree.insert("H");

function printNode(node) {
  process.stdout.write(`${node.value} -> `);
}

tree.inOrderTraverse(printNode);
tree.remove("H");
tree.inOrderTraverse(printNode);
tree.remove("D");
tree.inOrderTraverse(printNode);
tree.remove("F");
tree.inOrderTraverse(printNode);

console.log(tree.root);
```

---

# 그래프

- 정점과 간선으로 구성되어 네트워크 구조를 추상화한 비선형 자료 구조
- 정점(Vertex)과 간선(Edge)의 집합
- 다양한 그래프 종류를 혼합하여 표현 가능
- 길찾기, 게임, 지도, 네비게이션, 네트워크 등 문제에서 사용

## 방향 그래프

```js
/* 방향 그래프 */
// Graph(): edge object 객체 저장을 위한 생성자
// key: vertex
// value: list 형태로 연결된 vertex를 표현하여 edge 연결 관계 표현
function Graph() {
  this.edge = {};
}

// addVertex(): 정점(Vertex) 추가
Graph.prototype.addVertex = function (v) {
  this.edge[v] = [];
};

// addEdge(): 간선(Edge) 추가
Graph.prototype.addEdge = function (v1, v2) {
  this.edge[v1].push(v2);
};

// removeEdge(): 간선(edge) 삭제
Graph.prototype.removeEdge = function (v1, v2) {
  if (this.edge[v1]) {
    let idx = this.edge[v1].indexOf(v2);

    if (idx != -1) {
      this.edge[v1].splice(idx, 1);
    }

    if (this.edge[v1].length === 0) {
      delete this.edge[v1];
    }
  }
};

// removeVertex(): 정점(vertex) 삭제
Graph.prototype.removeVertex = function (v) {
  if (this.edge[v] === undefined) return;

  let length = this.edge[v].length;
  let connectedVertex = [...this.edge[v]];

  for (let i = 0; i < length; i++) {
    this.removeEdge(v, connectedVertex[i]);
  }
};

// sizeVertex(): vertex 개수 반환
Graph.prototype.sizeVertex = function () {
  return Object.keys(this.edge).length;
};

// sizeEdge(): edge 개수 반환
Graph.prototype.sizeEdge = function (vertex) {
  return this.edge[vertex] ? Object.keys(this.edge[vertex]).length : 0;
};

// print(): 현재 Graph 연결 상태 출력
Graph.prototype.print = function () {
  for (let vertex in this.edge) {
    let neighbors = this.edge[vertex];
    if (neighbors.length === 0) continue;

    process.stdout.write(`${vertex} -> `);
    for (let j = 0; j < neighbors.length; j++) {
      process.stdout.write(`${neighbors[j]} `);
    }
    console.log("");
  }
};

let graph = new Graph();
let vertices = ["A", "B", "C", "D", "E"];

for (let i = 0; i < vertices.length; i++) {
  graph.addVertex(vertices[i]);
}

graph.addEdge("A", "B");
graph.addEdge("A", "C");
graph.addEdge("A", "D");
graph.addEdge("C", "G");
graph.addEdge("D", "G");
graph.addEdge("D", "H");
graph.addEdge("B", "E");
graph.addEdge("B", "F");
graph.addEdge("E", "I");
graph.print();
console.log("");

graph.removeEdge("B", "F");
graph.removeEdge("B", "E");
graph.print();
console.log("");

graph.removeVertex("B");
graph.print();
console.log("");

graph.removeVertex("D");
graph.print();
console.log("");

console.log(graph.sizeVertex());
console.log(graph.sizeEdge("C"));
console.log(graph.sizeEdge("J"));
```

## 무방향 그래프

```js
/* 무방향 그래프 */
// Graph(): edge object 객체 저장을 위한 생성자
// key: vertex
// value: list 형태로 연결된 vertex를 표현하여 edge 연결 관계 표현
function Graph() {
  this.edge = {};
}

// addVertex(): 정점(Vertex) 추가
Graph.prototype.addVertex = function (v) {
  this.edge[v] = [];
};

// addEdge(): 간선(Edge) 추가
Graph.prototype.addEdge = function (v1, v2) {
  this.edge[v1].push(v2); // v1 -> v2
  this.edge[v2].push(v1); // v2 -> v1
};

// removeEdge(): 간선(edge) 삭제
Graph.prototype.removeEdge = function (v1, v2) {
  // v1 -> v2 삭제
  if (this.edge[v1]) {
    let idx = this.edge[v1].indexOf(v2);

    if (idx != -1) {
      this.edge[v1].splice(idx, 1);
    }

    if (this.edge[v1].length === 0) {
      delete this.edge[v1];
    }
  }
  // v2 -> v1 삭제
  if (this.edge[v2]) {
    let idx = this.edge[v2].indexOf(v1);

    if (idx != -1) {
      this.edge[v2].splice(idx, 1);
    }

    if (this.edge[v2].length === 0) {
      delete this.edge[v2];
    }
  }
};

// removeVertex(): 정점(vertex) 삭제
Graph.prototype.removeVertex = function (v) {
  if (this.edge[v] === undefined) return;

  let length = this.edge[v].length;
  let connectedVertex = [...this.edge[v]];

  for (let i = 0; i < length; i++) {
    this.removeEdge(v, connectedVertex[i]);
  }
};

// sizeVertex(): vertex 개수 반환
Graph.prototype.sizeVertex = function () {
  return Object.keys(this.edge).length;
};

// sizeEdge(): edge 개수 반환
Graph.prototype.sizeEdge = function (vertex) {
  return this.edge[vertex] ? Object.keys(this.edge[vertex]).length : 0;
};

// print(): 현재 Graph 연결 상태 출력
Graph.prototype.print = function () {
  for (let vertex in this.edge) {
    let neighbors = this.edge[vertex];
    if (neighbors.length === 0) continue;

    process.stdout.write(`${vertex} -> `);
    for (let j = 0; j < neighbors.length; j++) {
      process.stdout.write(`${neighbors[j]} `);
    }
    console.log("");
  }
};

let graph = new Graph();
let vertices = ["A", "B", "C", "D", "E", "F", "G", "H", "I"];

for (let i = 0; i < vertices.length; i++) {
  graph.addVertex(vertices[i]);
}

graph.addEdge("A", "B");
graph.addEdge("A", "C");
graph.addEdge("A", "D");
graph.addEdge("C", "G");
graph.addEdge("D", "G");
graph.addEdge("D", "H");
graph.addEdge("B", "E");
graph.addEdge("B", "F");
graph.addEdge("E", "I");
graph.print();
console.log("");

graph.removeEdge("B", "F");
graph.removeEdge("B", "E");
graph.print();
console.log("");

graph.removeVertex("B");
graph.print();
console.log("");

graph.removeVertex("D");
graph.print();
console.log("");

console.log(graph.sizeVertex());
console.log(graph.sizeEdge("C"));
console.log(graph.sizeEdge("J"));
```

---

# DFS (Depth First Search)

- 트리나 그래프 등에서 하나의 노드를 최대한 깊게 들어가면서 해를 찾는 탐색 기법
- 장점 : 인접한 후보 노드만 기억하면 되므로 적은 기억공간 소요, 노드가 깊은 단계에 있을 경우 빠르게 정답 산출
- 단점 : 선택한 경로가 답이 아닐 경우 불필요한 탐색 가능, 최단 경로를 구할 시 찾은 해가 정답이 아닐 경우 발생

```js

```

---

# 정렬

- 배열 내 원소들을 번호순이나 사전 순서와 같이 일정한 순서대로 열거하는 알고리즘
- 대표 정렬 알고리즘 별 구현 함수

## 거품정렬(BubbleSort)

- 서로 인접한 두 원소를 비교하면서 정렬하는 알고리즘
- O(n^2)

```js
let swap = function (arr, idx_1, idx_2) {
  let tmp = arr[idx_1];
  arr[idx_1] = arr[idx_2];
  arr[idx_2] = tmp;
};

let bubbleSort_1 = function (arr) {
  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = 0; j < arr.length - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        swap(arr, j, j + 1);
      }
    }
  }
};

let bubbleSort_2 = function (arr) {
  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = 0; j < arr.length - i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        swap(arr, j, j + 1);
      }
    }
  }
};

let bubbleSort_3 = function (arr) {
  let swapped;
  for (let i = 0; i < arr.length - 1; i++) {
    swapped = false;
    for (let j = 0; j < arr.length - i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        swap(arr, j, j + 1);
        swapped = true;
      }
    }
    if (!swapped) break;
  }
};
```

```js
let swap = function (arr, idx_1, idx_2) {
  let tmp = arr[idx_1];
  arr[idx_1] = arr[idx_2];
  arr[idx_2] = tmp;
};

let ascending = function (x, y) {
  return x > y;
};

let descending = function (x, y) {
  return x < y;
};

let bubbleSort = function (arr, compare) {
  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = 0; j < arr.length - i - 1; j++) {
      if (compare(arr[j], arr[j + 1])) {
        swap(arr, j, j + 1);
      }
    }
  }
};

/* test code */
let init_array = [6, 5, 1, 3, 2, 4];
let array;

let sorting = [bubbleSort];
let order = [ascending, descending];
for (let i = 0; i < sorting.length; i++) {
  for (let j = 0; j < order.length; j++) {
    console.log(sorting[i].name, order[j].name);

    array = [...init_array];
    sorting[i](array, order[j]);
    console.log(array);
  }
}
```

## 선택 정렬

- 최소값을 찾아 데이터 영역의 가장 앞으로 이동하는 방식을 반복하여 전체 데이터 영역을 정렬하는 알고리즘
- O(n^2)

```js
let selectionSort = function (arr, compare) {
  for (let i = 0; i < arr.length; i++) {
    let k = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (compare(arr[k], arr[j])) k = j;
    }
    swap(arr, i, k);
  }
};
```

## 삽입 정렬

- 이미 정렬된 데이터 영역과 비교하면서, 자신의 위치를 찾아 요소를 삽입하며 정렬하는 알고리즘
- O(n^2)

```js
let insertionSort = function (arr, compare) {
  for (let i = 1; i < arr.length; i++) {
    let tmp = arr[i];
    let j;
    for (j = i - 1; j >= 0; j--) {
      arr[j + 1] = arr[j];
      if (compare(tmp, arr[j])) {
        break;
      }
    }
    arr[j + 1] = tmp;
  }
};
```

## 병합 정렬

- 하나의 배열을 두 개의 균등한 크기로 분할하고, 부분 정렬하며, 이를 다시 합하면서 전체를 정렬해가는 알고리즘
- O(n log n)

```js
let mergeSort = function (arr, compare) {
  if (arr.length === 1) return arr;

  let m = (arr.length / 2).toFixed(0);
  let left = mergeSort(arr.slice(0, m), compare);
  let right = mergeSort(arr.slice(m), compare);

  let i = 0,
    j = 0,
    k = 0;
  while (i < left.length && j < right.length) {
    arr[k++] = compare(left[i], right[j]) ? right[j++] : left[i++];
  }
  while (i < left.length) arr[k++] = left[i++];
  while (j < right.length) arr[k++] = right[j++];

  return arr;
};
```

## 퀵 정렬

- 특정한 값을 기준으로 큰 숫자와 작은 숫자를 분할하여 정렬하는 알고리즘
- O(n log n)

```js
let quickSort = function (arr, compare, s = 0, e = arr.length - 1) {
  let start = s;
  let pivot = arr[e];

  for (let i = s; i <= e; i++) {
    if (compare(pivot, arr[i])) {
      swap(arr, start, i);
      start++;
    }
  }
  swap(arr, start, e);

  if (start - 1 > s) quickSort(arr, compare, s, start - 1);
  if (start + 1 < e) quickSort(arr, compare, start + 1, e);
};
```

## 이진 검색

- 자료 구조 기반으로 정렬되어 있는 데이터 안에서 특정 값을 찾는 기법
- O(log n)
