### 문제

- 문자열을 감안할 때 s바로 문자를 포함 `(`, `)`, `{`, `}`, `[`, `]` 입력 문자열이 유효한지 구하시오.

1. 열린 브래킷은 동일한 유형의 브래킷으로 닫아야 합니다.

2. 열린 브래킷은 올바른 순서로 닫아야 합니다.

### 제약 사항

### 풀이

```js
const validParentheses = (s) => {
  // 문자열이 없거나, 괄호 개수가 안맞으면 false
  const sLen = s.length;
  if (sLen === 0 || sLen % 2 !== 0) return false;

  // 문자열 길이가 2이면, 괄호가 정상적인지 판단한다.
  if (sLen === 2) return ["()", "{}", "[]"].includes(s);

  const obj = {
    "(": ")",
    "{": "}",
    "[": "]",
  };

  //  정상적인 괄호를 찾아내는 반복문
  let stack = [];
  for (let i = 0; i < s.length; i++) {
    if (obj[s[i]]) {
      stack.push(s[i]);
    } else {
      const last = stack.pop();
      if (obj[last] !== s[i]) return false;
    }
  }

  // 문자열을 순서대로 제거하고, 남은 문자열이 없으면 true
  return stack.length === 0 ? true : false;
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/131074636-1005b762-744d-4969-82c3-890495de4b70.png)
