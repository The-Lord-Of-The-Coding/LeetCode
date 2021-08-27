### 문제

- 부호 있는 32비트 정수가 주어지면 숫자를 반대로 반환 하시오.

### 제약 사항

- [-2^31, 2^31 - 1] = 0 ‣ `Math.pow(2, 31) - 1`

### 풀이

```js
const reverse = (x) => {
  // 32 비트 정수 최대 값 정의
  const LIMIT = Math.pow(2, 31) - 1;

  // 입력받은 데이터를 절대값으로 변경한 후, 문자열 reverse()를 통해 역전 시킨다.
  let result = 0;
  result = parseInt(Math.abs(x).toString().split("").reverse().join(""));

  // 역전한 데이터와 최대 값을 비교하여 초과시, 0 반환
  if (result > LIMIT) return 0;

  // 입력 값이 양수, 음수인지 판단한다.
  let flag = true;
  if (x < 0) flag = false;

  // 입력 값이 음수 일 경우, 음수로 변환한다.
  return flag ? result : result * -1;
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/130929066-daa72ea3-1ceb-47e7-bd43-35b83af59730.png)
