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
