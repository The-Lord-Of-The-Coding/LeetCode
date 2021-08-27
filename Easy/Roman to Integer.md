### 문제

- 로마 숫자는 일곱 가지 기호로 표시하는데, 그것을 정수로 변환하십시오.

### 제약 사항

- 로마 숫자는 일반적으로 왼쪽에서 오른쪽으로 큰 것에서 작은 것 순으로 표기합니다. ‣ `reverse()를 통해, 역전하여 계산`

### 풀이

```js
const romanToInt = (s) => {
  const Romans = {
    I: 1,
    V: 5,
    X: 10,
    L: 50,
    C: 100,
    D: 500,
    M: 1000,
  };

  // reverse()를 통해 역전 시킨다.
  const reverseArray = s.split("").reverse();

  // 로마 문자를 숫자로 변환한다.
  const numberArray = reverseArray.map((item) => Romans[item]);

  // 반복문을 통해, 이전 값을 저장하고 비교하여 클 경우 더하고, 작을 경우 뺀다.
  let temp = 0;
  let total = 0;
  for (let i = 0; i < numberArray.length; i++) {
    const num = numberArray[i];

    if (num >= temp) {
      total += num;
      temp = num;
    } else {
      total -= num;
    }
  }

  return total;
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/130936897-30432914-695d-4b1f-b5d2-87b3d32a7fde.png)
