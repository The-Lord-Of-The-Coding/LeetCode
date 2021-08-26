### 문제

- 문자열 배열 중에서 가장 긴 공통 접두사 문자열을 찾는 함수를 작성하십시오.
- 공통 접두사가 없으면 빈 문자열을 반환합니다.

### 제약 사항

### 풀이

```js
const longestCommonPrefix = (strs) => {
  // 배열에 데이터가 없을 경우, 빈값 반환
  if (strs.length === 0) return "";

  // 배열 알파벳 순으로 정렬, 첫번째, 마지막 배열 데이터를 변수에 저장
  const sortString = strs.sort();
  const fristString = sortString[0];
  const lastString = sortString[sortString.length - 1];

  // 반복문을 통해, 첫번째, 마지막 배열 문자열을 단어 단위로 비교하면서, 카운트 증가
  let i = 0;
  while (
    i < fristString.length &&
    fristString.charAt(i) == lastString.charAt(i)
  )
    i++;

  // 문자열이 같은 개수 만큼, 문자열 자르고 반환
  return fristString.substring(0, i);
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/130948099-1c7674b4-95a3-4ea2-8215-5ef0924a744d.png)
