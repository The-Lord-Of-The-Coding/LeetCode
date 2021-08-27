### 문제

- 정수는 정방향과 역방향이 같은 지 반환하시오.

### 제약 사항

### 풀이

```js
const isPalindrome = (x) => {
  // 음수이면, false 반환
  if (x < 0) return false;

  // 0이면, true 반환
  if (x === 0) return true;

  // 맨 끝자리가 0일 경우, false 반환 예) 10은 01로 넘버 비교가 안되는 사항으로 false
  if (x % 10 === 0) return false;

  // 문자열 reverse()를 통해 역전 시킨다.
  const reseverNum = parseInt(x.toString().split("").reverse().join(""));

  // 입력 받은 값과 역전한 값을 비교
  return x === reseverNum;
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/130928777-32d6e284-536e-4e8d-8b60-4dd476e6c38b.png)
