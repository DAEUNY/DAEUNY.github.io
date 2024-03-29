---
title:  "[프로그래머스] Lv.0 리스트 자르기"
excerpt: ""

categories:
  - TIL
tags:
  - [TIL, PROGRAMMERS-풀이]

toc: true
toc_sticky: true
 
date: 2024-01-12
last_modified_at: 2024-01-12
---

### 문제

정수 `n`과 정수 3개가 담긴 리스트 `slicer` 그리고 정수 여러 개가 담긴 리스트 `num_list`가 주어집니다. `slicer`에 담긴 정수를 차례대로 a, b, c라고 할 때, `n`에 따라 다음과 같이 `num_list`를 슬라이싱 하려고 합니다.

- `n = 1` : `num_list`의 0번 인덱스부터 `b`번 인덱스까지
- `n = 2` : `num_list`의 `a`번 인덱스부터 마지막 인덱스까지
- `n = 3` : `num_list`의 `a`번 인덱스부터 `b`번 인덱스까지
- `n = 4` : `num_list`의 `a`번 인덱스부터 `b`번 인덱스까지 `c` 간격으로

올바르게 슬라이싱한 리스트를 return하도록 solution 함수를 완성해주세요.

---

### 제한사항

- `n` 은 1, 2, 3, 4 중 하나입니다.
- `slicer`의 길이 = 3
- `slicer`에 담긴 정수를 차례대로 a, b, c라고 할 때
    - 0 ≤ a ≤ b ≤ `num_list`의 길이 - 1
    - 1 ≤ c ≤ 3
- 5 ≤ `num_list`의 길이 ≤ 30
- 0 ≤ `num_list`의 원소 ≤ 100

---

### 입출력 예

| n | slicer | num_list | result |
| --- | --- | --- | --- |
| 3 | [1, 5, 2] | [1, 2, 3, 4, 5, 6, 7, 8, 9] | [2, 3, 4, 5, 6] |
| 4 | [1, 5, 2] | [1, 2, 3, 4, 5, 6, 7, 8, 9] | [2, 4, 6] |

---

### 입출력 예 설명

입출력 예 #1

- [1, 2, 3, 4, 5, 6, 7, 8, 9]에서 1번 인덱스부터 5번 인덱스까지 자른 리스트는 [2, 3, 4, 5, 6]입니다.

입출력 예 #2

- [1, 2, 3, 4, 5, 6, 7, 8, 9]에서 1번 인덱스부터 5번 인덱스까지 2개 간격으로 자른 리스트는 [2, 4, 6]입니다.
---

### 풀이

> `[a, b, c]` 에 slicer를 할당해주고 시작
> 
> 
> `n`이 무슨  숫자인지에 따라 slice 해주고, 
> 
> 조건문을 삼항연산자로 사용해서 각 반환할 배열을 만들어주었다.
> 


```jsx
function solution(n, slicer, num_list) {
    let [a, b, c] = slicer
    
    return n === 1 
        ? num_list.slice(0, b+1)
        : n === 2 
            ? num_list.slice(a)
            : n === 3 
                ? num_list.slice(a, b+1)
                : num_list.slice(a, b+1).filter((_, i) => i % c === 0)
}
```

### 시행착오

> 처음 구조분해할당을 해두고도,
> 
> 
> 반환문에는 신경쓰지않고 다시 각각 `slicer`를 `map()`으로 돌면서 a, b, c를 사용하다가
> 
> 분명 틀리진 않았는데 테스트 에러남
> 
> 제출하기 돌려보니 전부 런타임 에러로 떠서 저렇게 꼬리물기 방식은 좋지 않겠다…
> 
> 싶긴하지만 또 다른건 고치지 않고 `map`만 없애줌. 
> 
> 바로 `a, b, c` 변수를 사용해서 `slice()` 사용!
> 
> 조금 트리키했던게 마지막 경우인데,
> 
> 이 부분도 처음에는 `v % 4 === 0`으로 하니 3번, 19번이 틀렸다고 나옴.
> 
> 예시만 봐도 알수 있지만,, 간격이 `c`여야지, 해당 값이 `c`의 배수는 아니기 때문에 
> 
> 당연히 틀림,,, 
> 
> 미리 생각하자! 
> 

### 느낀 점

> 런타임에 대해 생각해보자
> 
> 
> 다른 사람들 풀이는 대부분 switch를 사용했던데,
> 
> + 많이 써보지 않아서 쓸 시도를 잘 안해보고 있다,,
> 
> 풀이 보고 따라해본 뒤 블로그도 수정하자! 
>