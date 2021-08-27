### 문제

- strStr() 메서드를 구현하시오.

### 제약 사항

- 내장된 메서드를 사용하지 않고, 알고리즘을 작성해보자

- indexOf() 내장 메서드를 사용하는건 알고리즘 공부에 효과적인지 않다고 판단

### 풀이

```js
const strStr = (haystack, needle) => {
  // 두 문자가 동일하면, 0 반환
  if (haystack === needle) return 0;

  // needle 문자가 없을 경우, 0 반환
  if (needle === "") return 0;

  // 비교 문자가 비교 대상 문자보다 길이가 클 경우, -1 반환
  if (haystack.length < needle.length) return -1;

  /**
   * 반복문을 통해, needle 첫 문자가 일치하는 haystack 배열 위치를 찾고,
   * needle 길이만큼 반복하면서, haystack 위치랑 번갈아 비교
   * 같은 문자 개수와 needle 길이가 같으면, 해당 i의 위치를 반환,
   */
  for (let i = 0; i < haystack.length; i++) {
    if (haystack[i] === needle[0]) {
      let j = 0;
      while (j < needle.length) {
        if (haystack[i + j] !== needle[j]) break;
        j++;
      }

      if (j === needle.length) return i;
    }
  }

  // 모든 문자가 다르면, -1 반환
  return -1;
};
```

### 결과

![](https://user-images.githubusercontent.com/42952358/131094885-7c114f33-bc1d-42b1-9f7e-766e463b75ee.png)

---

### 참고 사항

`Exdeath` 님이 올려주신 [코드](https://leetcode.com/problems/implement-strstr/discuss/590911/JavaScript-solution.-No-built-in-methods.)로 내가 작성한 코드와 매우 흡사하나, RunTime 두배 이상 차이가 났다.

특이점으로 가장 보인 내용은 반복문의 조건식이 `haystack` 문자열 길이와 `needle` 문자열 길이를 뺀 길이로 한다는 점이였다.

그렇게도, 반복문을 `haystack`까지 전부 할 필요도 없이, 적은 동작으로 할 수 있는 점에서 많은 시간이 단축된 것을 확인 할 수 있었다.

```js
const strStr = (haystack, needle) => {
  if (needle === "" || needle === haystack) return 0; // the only mandatory check here is (needle === '')
  if (haystack.length < needle.length) return -1; // the other ones are for efficiency

  for (let i = 0; i < haystack.length - needle.length + 1; i++) {
    // start looping through haystack until the remaining substring is shorter than needle
    if (haystack[i] === needle[0]) {
      // as soon as we see a character that matches the first character of needle
      for (let j = 0; j < needle.length; j++) {
        // start looping through both needle and haystack
        if (needle[j] !== haystack[i + j]) {
          // as soon as the characters don't match
          break; // break out of the loop and return to looping through haystack
        } else if (j === needle.length - 1) {
          // otherwise, if we looped through the entire needle and all of the characters matched
          return i; // return the index of the first character of haystack with which we started the loop
        }
      }
    }
  }

  return -1; // return -1 if there wasn't a match
};
```

![](https://user-images.githubusercontent.com/42952358/131096207-b20bc885-81cf-4d43-8941-8d9f5ea15ed1.png)

---

## 최종

그러하여, 내가 작성에 코드에 `Exdeath`님 코드를 참고하여 반복문에 조건식을 수정 해보았다.

놀랍게도 이전 RunTime에 ¼ 단축 된 것을 확인 할 수 있었다.

```js
const strStr = (haystack, needle) => {
  // 두 문자가 동일하면, 0 반환
  if (haystack === needle) return 0;

  // needle 문자가 없을 경우, 0 반환
  if (needle === "") return 0;

  // 비교 문자가 비교 대상 문자보다 길이가 클 경우, -1 반환
  if (haystack.length < needle.length) return -1;

  /**
   * 반복문을 통해, needle 첫 문자가 일치하는 haystack 배열 위치를 찾고,
   * needle 길이만큼 반복하면서, haystack 위치랑 번갈아 비교
   * 같은 문자 개수와 needle 길이가 같으면, 해당 i의 위치를 반환, 아니면 0 반환
   */
  for (let i = 0; i < haystack.length - needle.length + 1; i++) { << // 해당 조건식 수정
    if (haystack[i] === needle[0]) {
      let j = 0;
      while (j < needle.length) {
        if (haystack[i + j] !== needle[j]) break;
        j++;
      }

      if (j === needle.length) return i;
    }
  }

  // 모든 문자가 다르면, -1 반환
  return -1;
};
```

![](https://user-images.githubusercontent.com/42952358/131097294-70a6403c-9d33-4282-84b7-3bdb1fad78c1.png)
