---
title:  "[프로그래머스] Lv.0 코드 처리하기"
excerpt: ""

categories:
  - TIL
tags:
  - [TIL, PROGRAMMERS-풀이]

toc: true
toc_sticky: true
 
date: 2024-01-13
last_modified_at: 2024-01-13
---


### 문제

문자열 `code`가 주어집니다.

`code`를 앞에서부터 읽으면서 만약 문자가 "1"이면 `mode`를 바꿉니다. `mode`에 따라 `code`를 읽어가면서 문자열 `ret`을 만들어냅니다.

`mode`는 0과 1이 있으며, `idx`를 0 부터 `code의 길이 - 1` 까지 1씩 키워나가면서 `code[idx]`의 값에 따라 다음과 같이 행동합니다.

- `mode`가 0일 때
    - `code[idx]`가 "1"이 아니면 `idx`가 짝수일 때만 `ret`의 맨 뒤에 `code[idx]`를 추가합니다.
    - `code[idx]`가 "1"이면 `mode`를 0에서 1로 바꿉니다.
- `mode`가 1일 때
    - `code[idx]`가 "1"이 아니면 `idx`가 홀수일 때만 `ret`의 맨 뒤에 `code[idx]`를 추가합니다.
    - `code[idx]`가 "1"이면 `mode`를 1에서 0으로 바꿉니다.

문자열 `code`를 통해 만들어진 문자열 `ret`를 return 하는 solution 함수를 완성해 주세요.

단, 시작할 때 `mode`는 0이며, return 하려는 `ret`가 만약 빈 문자열이라면 대신 "EMPTY"를 return 합니다.

---

### 제한사항

- 1 ≤ `code`의 길이 ≤ 100,000
    - `code`는 알파벳 소문자 또는 "1"로 이루어진 문자열입니다.

---

### 입출력 예

| code | result |
| --- | --- |
| "abc1abc1abc" | "acbac" |

---

### 입출력 예 설명

입출력 예 #1

- `code`의 각 인덱스 `i`에 따라 다음과 같이 `mode`와 `ret`가 변합니다.

| i | code[i] | mode | ret |
| --- | --- | --- | --- |
| 0 | "a" | 0 | "a" |
| 1 | "b" | 0 | "a" |
| 2 | "c" | 0 | "ac" |
| 3 | "1" | 1 | "ac" |
| 4 | "a" | 1 | "ac" |
| 5 | "b" | 1 | "acb" |
| 6 | "c" | 1 | "acb" |
| 7 | "1" | 0 | "acb" |
| 8 | "a" | 0 | "acba" |
| 9 | "b" | 0 | "acba" |
| 10 | "c" | 0 | "acbac" |


따라서 "acbac"를 return 합니다.

### 풀이

> 
> 
> 먼저 시작할 때의 `mode`를 정의해주었다
> 
> `code` 각 문자를 하나씩 쪼개 배열에 넣어준 뒤, 
> 
> `filter()` 를 통해 각 `mode`의 조건에 맞는 문자만을 남기도록 했다.
> 
> (`filter()` 안에서 `mode` 변경 먼저!)
> 
> 조건에 맞는 문자가 하나도 없을 때 “EMPTY”를 반환해야 하기 때문에
> 
> 마지막 반환문에서는 다시 삼항연산자로 조건식을 작성했다
>

```jsx
function solution(code) {   
    
    let mode = code[0] === 0 ? 1 : 0
    
    
    code = code
        .split('')
        .filter((v, i) => {
            if (v === '1') {
                mode = mode === 0 ? 1 : 0
                return 0;
            }
            return i % 2 === mode
            // if (mode === 0) return i % 2 === 0
            // if (mode === 1) return i % 2 !== 0
            })
        .join('')
        
    return code.length === 0 ? "EMPTY" : code
    
}
```

### 풀이 (다른 사람의 풀이 참고)

> mode를 숫자가 아니라 boolean 값으로 대체하면 훨씬 간단하게 코드 작성할 수 있다!
> 

```jsx
function solution(code) {
    let answer = "";
    let mode = true;
    
    code.split('').map((v, i) => v === '1' 
                       ? mode = !mode
                       : answer += !(i % 2) === mode ? v : ""
                      )
    
    return answer || "EMPTY"
    
}
```


### 배운 점

> 반복 사용되는 수식은 하나의 수식으로 적용할 수 있는 방법이 있을지 먼저 고민해보자!
> 
> `return i % 2 === mode`
> 
> 위 리턴문과 아래 두 리턴문의 결과가 같다… 
> 
> 당연… 
> 
> 조건문 안에 작성한 내용과 나머지의  결과값이 같으니..! 
> 
> `if (mode === 0) return i % 2 === 0`
> 
> `if (mode === 1) return i % 2 !== 0`
>