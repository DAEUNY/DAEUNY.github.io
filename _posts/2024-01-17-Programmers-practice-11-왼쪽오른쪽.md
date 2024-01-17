---
title:  "[프로그래머스] Lv.0 왼쪽 오른쪽"
excerpt: ""

categories:
  - TIL
tags:
  - [TIL, PROGRAMMERS-시행착오]

toc: true
toc_sticky: true
 
date: 2024-01-17
last_modified_at: 2024-01-17
---


### 문제

문자열 리스트 `str_list`에는 "u", "d", "l", "r" 네 개의 문자열이 여러 개 저장되어 있습니다. `str_list`에서 "l"과 "r" 중 먼저 나오는 문자열이 "l"이라면 해당 문자열을 기준으로 왼쪽에 있는 문자열들을 순서대로 담은 리스트를, 먼저 나오는 문자열이 "r"이라면 해당 문자열을 기준으로 오른쪽에 있는 문자열들을 순서대로 담은 리스트를 return하도록 solution 함수를 완성해주세요. "l"이나 "r"이 없다면 빈 리스트를 return합니다.

---

### 제한사항

- 1 ≤ `str_list`의 길이 ≤ 20
- `str_list`는 "u", "d", "l", "r" 네 개의 문자열로 이루어져 있습니다.

---

### 입출력 예

| str_list | result |
| --- | --- |
| ["u", "u", "l", "r"] | ["u", "u"] |
| ["l"] | [] |

---

### 입출력 예 설명

입출력 예 #1

- "r"보다 "l"이 먼저 나왔기 때문에 "l"의 왼쪽에 있는 문자열들을 담은 리스트인 ["u", "u"]를 return합니다.

입출력 예 #2

- "l"의 왼쪽에 문자열이 없기 때문에 빈 리스트를 return합니다.


### 풀이

> `“l”` 또는 `“r”` 의 인덱스를 찾는다
> 
> 
> 인덱스가 없다면, 빈 배열을 리턴한다
> 
> 해당 인덱스의 문자가 `“l”`일 경우와 `“r”`일 경우로 나눠 결과를 반환한다.
> 

```jsx
function solution(str_list) {
    let idx = str_list.findIndex(e => e === "l" || e === "r")
    if (idx === -1) return []
    else if (str_list[idx] === "l") return str_list.slice(0, idx)
    else if (str_list[idx] === "r") return str_list.slice(idx+1)
}
```


### 다른 풀이

> 
> 

```jsx
let idx = str_list.findIndex(e => /l|r/.test(e))
    if (idx === -1) return []
    return str_list[idx] === "l" ? str_list.slice(0, idx) : str_list.slice(idx+1)
```

### 시행착오 (틀린 코드)

> 각 문자와 인덱스를 동시에 아는 방법으로 풀려고 시도했다
> 
> 
> 처음엔 `map()`을 사용하려고 `splice()` 를 써서 원배열을 수정해준 후, 원 배열을 반환했다
> 
> 75점이 나왔다… (10번 이후로 반 이상 틀림)
> 
> 질문하기를 많이 참고해보니 `“r”` 이 먼저 나오는 경우 
> 
> 이후에 포함된 문자열에 `“l”` 이 있을 수도 있어서 문제가 된다.
> 
> 그래서 마지막 줄에 `filter()`를 추가해 `“l”`을 필터링하는 코드까지 추가했는데,,
> 
> 그래도 틀렸다ㅠㅠ 
> 
> 더이상 뭐가 문제인지 모르겠고,, 
> 
> 결국 `findIndex()`를 써서 다른 방식으로 인덱스를 찾아 문제를 풀었다.
> 
> 아래 식이 안되는 이유는 뭘까ㅠㅠ 
> 
> `“l”` 과 `“r”`이 없는 경우를 위의 풀이와 똑같이 `findIndex()`를 쓰고
> 
> `if (idx === -1) return []` 해줬는데도 안되는것 보면 
> 
> 아래 `map()` 에서 문제가 있다는 건데,,
> 
> ```jsx
> function solution(str_list) {
> 		if (!str_list.includes("l") && !str_list.includes("r")) return []
> 		    str_list.map((v, i) => v === "l" 
> 		                        ? str_list.splice(i) 
> 		                        : v === "r" 
> 		                            ? str_list.splice(0, i+1) : v)
> 		    return str_list.filter(e => e!== "l")
> }
> ```
>