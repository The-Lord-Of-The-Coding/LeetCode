### 문제

- 주어진 문자의 마지막 단어의 길이를 구하시오.

### 제약 사항

### 풀이

```js
const lengthOfLastWord = (s) => {
  s = s.trim();

  if (s.length === 0) return 0;

  let len = 0;
  for (let i = s.length - 1; i >= 0; i--) {
    if (s[i] === " ") break;
    len++;
  }

  return len;
};
```

### 결과

![image](https://user-images.githubusercontent.com/42952358/131321230-f34f1ea6-1ba9-4939-8bda-def8176e54fc.png)

## 추가사항

```js
const lengthOfLastWord = (s) => {
  return s.trim().split(" ").pop().length;
};
```

![image](https://user-images.githubusercontent.com/42952358/131321323-ba66bb0f-768e-4efc-a53b-7746a1eb27f7.png)
