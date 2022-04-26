## 제로베이스 코테 정리

map.get , map.set 활용 잘하기

```js
console.log(a.toString(2).match(/1/gi).length);
```

```js
function compare(a, b) {
  let aValue = a == 0 ? a : a.toString(2).match(/1/gi).length;
  let bValue = b == 0 ? b : b.toString(2).match(/1/gi).length;
  console.log(b);

  if (aValue == bValue) {
    return a - b;
  } else {
    return aValue - bValue;
  }
}

function solution(A) {
  return A.sort(compare);
}
```

- 제곱근이 정수면 약수의 개수는 홀수
