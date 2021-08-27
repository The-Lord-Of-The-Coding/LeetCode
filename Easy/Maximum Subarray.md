### 문제

- 정수 배열이 주어졌을 때, 가장 큰 합을 갖는 연속적인 배열을 찾아 그 합을 반환하시오.

### 제약 사항

### 풀이

```js
const maxSubArray = (nums) => {
  // 배열의 길이가 0인 경우, 0을 반환
  if (nums.length === 0) return 0;

  // 배열의 길이가 1인 경우, 배열의 첫번째 원소를 반환
  if (nums.length === 1) return nums[0];

  // 배열의 값이 모두 음수인 경우, 최대값을 반환
  if (nums.every((num) => num < 0)) return Math.max(...nums);

  /**
   * 반복문을 통해, 각 원소를 배열의 첫번째 원소부터 끝에서부터 검사하며,
   * 순차적으로 더한 값을 이전 값과 비교하면서, 최대값을 구하며, 추가적으로 배열의 위치도 같이 저장한다.
   */
  let to = 0,
    from = 0,
    temp = 0;
  for (let i = 0; i < nums.length; i++) {
    let j = i,
      sum = 0;
    while (j < nums.length) {
      sum += nums[j];
      if (temp < sum) {
        to = i;
        from = j;
        temp = sum;
      }
      j++;
    }
  }

  return temp;
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/131139077-5bd1782b-b1ad-44e1-86a2-1546fbf018af.png)

---

### 참고 사항

`cenkay` 님이 올려주신 [코드](https://leetcode.com/problems/maximum-subarray/discuss/139218/Javascript-very-clear-and-short-DP-solution)로 내가 작성한 코드와 비교하여 보였다. 확실히 성능적으로 우세하였다.

그러나, 개인적으로 아쉬웠던 점은 내부 메서드를 사용하여 작성한 코드라 내가 원하는 코드는 아니였다.

개인적으로 공부를 목적으로 진행한 사항이라, 최대한 내부 메서드를 사용하지 않고 구현을 해보고 싶었다.

하지만, 바퀴를 다시 만들지 않는다는 마인드로 적절한 경우 올바르게 사용하는게 좋다고도 생각한다.

참고삼아 코드를 올려본다.

```js
const maxSubArray = (nums) => {
  // 반복문을 통해, 현 배열값과 현 배열값과 이전 배열과 더한 값 중에 최대 값을 현 배열 값에 저장한다.
  for (let i = 1; i < nums.length; i++) {
    nums[i] = Math.max(nums[i], nums[i] + nums[i - 1]);
  }

  // 배열 값에서 최대 값 반환
  return Math.max(...nums);
};
```

![](https://user-images.githubusercontent.com/42952358/131142581-a76bc9f7-eed3-46cc-a1df-87a94cbee5c2.png)
