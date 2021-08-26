### 문제

- 정수의 배열을 순환하여, 입력한 값을 두 값을 더해서 만드는 값을 반환하시오.

### 제약 사항

### 풀이

```js
const twoSum = (nums, target) => {
  // nums 배열 순환
  for (let i = 0; i < nums.length; i++) {
    // nums i + 1 배열 순환
    for (let j = i + 1; j < nums.length; j++) {
      // 배열을 순서대로 순환하고 두 수를 더한 값이 target의 값이면 해당 index 값 반환
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/130928963-7c21f2db-827c-4487-952e-2d68e9627094.png)
