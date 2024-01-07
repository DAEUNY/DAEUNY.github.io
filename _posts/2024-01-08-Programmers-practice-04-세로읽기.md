---
title:  "[프로그래머스] Lv.0 세로 읽기"
excerpt: ""

categories:
  - TIL
tags:
  - [TIL]

toc: true
toc_sticky: true
 
date: 2024-01-08
last_modified_at: 2024-01-08
---


### 문제

문자열 `my_string`과 두 정수 `m`, `c`가 주어집니다. `my_string`을 한 줄에 `m` 글자씩 가로로 적었을 때 왼쪽부터 세로로 `c`번째 열에 적힌 글자들을 문자열로 return 하는 solution 함수를 작성해 주세요.

---


### 제한사항

- `my_string`은 영소문자로 이루어져 있습니다.
- 1 ≤ `m` ≤ `my_string`의 길이 ≤ 1,000
- `m`은 `my_string` 길이의 약수로만 주어집니다.
- 1 ≤ `c` ≤ `m`

---


### 입출력 예

| my_string | m | c | result |
| --- | --- | --- | --- |
| "ihrhbakrfpndopljhygc" | 4 | 2 | "happy" |
| "programmers" | 1 | 1 | "programmers" |

---

### 입출력 예 설명

입출력 예 #1

- 예제 1번의 `my_string`을 한 줄에 4 글자씩 쓰면 다음의 표와 같습니다.
    
    
    | 1열 | 2열 | 3열 | 4열 |
    | --- | --- | --- | --- |
    | i | h | r | h |
    | b | a | k | r |
    | f | p | n | d |
    | o | p | l | j |
    | h | y | g | c |
    
    2열에 적힌 글자를 세로로 읽으면 happy이므로 "happy"를 return 합니다.


    
  ### 풀이 (처음 푼 방식)

>  
> 
> 원 배열을 변경시키려고 splice()를 씀. 
> 
> 그래서 문자열을 배열로 바꾸기도 함
> 
> `m`개씩 끊어진 문자 배열에서 `c-1`번째 요소만 남기도록 한 다음
> 
> `join()` 을 사용해서 문자열로 변경
> 
> 복잡도 해라…
> 

```jsx
function solution(my_string, m, c) {
    let list = my_string.split('')
    return Array
        .from(
            {length : list.length / m}, 
            v => list.splice(0,m)
        )
            .map((v) => v[c-1])
            .join('')    
}
```

```jsx
const solution = (s, m, c) => s
		.match(new RegExp(`.{${m}}`,'g'))
		.map(v => v[c-1])
		.join('')
```

### 풀이 (다른 사람의 풀이 참고)

> 블로그 작성의  이유,,
> 

```jsx
function solution(my_string, m, c) {
    return [...my_string]
				.filter((v, i) => i % m + 1 === c)
				.join('')
}
```

### 후기

수학 계산을 먼저 생각하면 이렇게 간단하게 풀 수 있는데,,

이런 생각을 어떻게 하냐고???

화려한 수식보다 간단하지만 이런 수식이 들어간 코드가 더 자극이 된다..! 

프로그래머스에서 매일매일 문제를 풀다보니 다른 사람의 풀이를 볼 기회도 많으니

문제를 풀 때 이런 부분을 더 염두에 푸고  풀어보자! 

`i % m + 1 === c` …….