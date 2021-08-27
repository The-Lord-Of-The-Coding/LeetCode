### 문제

- 고유한 정수의 정렬된 배열과 대상 값이 주어지면 대상이 발견되면 인덱스를 반환하시오.

### 제약 사항

### 풀이

```js
const searchInsert = (nums, target) => {
  // nums의 배열이 존재하지 않으면 0을 반환한다.
  if (nums.length === 0) return 0;

  // target이 0인 경우, 0을 반환한다.
  if (target === 0) return 0;

  // 반복문을 통해, target과 같거나, 크면 해당 인덱스를 반환한다.
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] >= target) return i;
  }

  // nums의 배열이 target보다 작으면, 마지막 인덱스(배열 길이)를 반환한다.
  return nums.length;
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/131106337-65fbb738-0863-4f74-9416-edc91960cc1a.png)
