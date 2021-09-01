### 문제

- 주어진 배열 값 맨 마지막 값에 1을 더하시오.

### 제약 사항

- 맨 마지막 값이 9일 경우, 10으로 배열의 값이 없을 경우 0이 된다.

- 배열의 값이 없을 경우 1을 반환한다.

### 풀이

```js
const plusOne = (digits) => {
  for (let i = digits.length - 1; i >= 0; i--) {
    if (digits[i] === 9) {
      digits[i] = 0;
    } else {
      digits[i]++;
      return digits;
    }
  }

  return [1, ...digits];
};
```

### 결과

![image](https://user-images.githubusercontent.com/42952358/131321480-05b19c4a-5b7d-4e90-89a5-680d8b0af562.png)

##

```js
const plusOne = (digits) => {
  for (let i = digits.length - 1; i >= 0; i--) {
    if (++digits[i] > 9) digits[i] = 0;
    else return digits;
  }

  return [1, ...digits];
};
```

![image](https://user-images.githubusercontent.com/42952358/131321916-be6dc514-bcf7-4c51-a7ec-87cefb5b87ab.png)
