---
title:  "[프로그래머스] Lv.0 수 조작하기 1"
excerpt: ""

categories:
  - TIL
tags:
  - [TIL]

toc: true
toc_sticky: true
 
date: 2023-12-19
last_modified_at: 2023-12-19
---
## 문제 설명
---
정수 n과 문자열 control이 주어집니다. 

control은 "w", "a", "s", "d"의 4개의 문자로 이루어져 있으며, 

control의 앞에서부터 순서대로 문자에 따라 n의 값을 바꿉니다.


"w" : n이 1 커집니다.


"s" : n이 1 작아집니다.


"d" : n이 10 커집니다.


"a" : n이 10 작아집니다.


위 규칙에 따라 n을 바꿨을 때 가장 마지막에 나오는 n의 값을 return 하는 solution 함수를 완성해 주세요.


## 풀이 1 (처음 푼 방식)
---
> control에 문자로 주어진 값을 하나씩 쪼개 배열로 만든 뒤, 각 요소 별 더하거나 뺼 값을 계산해준다
>> error) 처음에 배열도 안 만들고 반복문도 없이 if문만 작성하는 뭔 뻘짓을...😨 오늘 계속 문제 풀고 있었는데 갑자기 정신을 어디다 둔건지ㅋㅋ큐ㅠ 


```
function solution(n, control) {
    var answer = 0;

    control.split('').map(e => {
        if (e === "w") {
            n = n + 1
        } else if (e === "s") {
            n = n - 1
        } else if (e === "d") {
            n = n + 10
        } else if (e === "a") {
            n = n - 10
        }
    })
  return n;
}
```


    
## 풀이 2 (다른 사람의 풀이 참고)
---
> 다른 사람들 풀이 보고 깔끔하고 간결하다고 생각되는 것 논리만 참고해서 풀어봄
> 
> 각 문자에 해당하는 값을 적용한 객체를 만들어준 뒤, reduce로 모든 값을 더해서 바로 반환


```
function solution(n, control) {
  const value = {
    "w" : 1,
    "s" : -1,
    "d" : 10,
    "a" : -10
  }
  
  return control.split('').reduce((a, c) => a + value[c],n)
}
```



<br>

> 객체를 사용하는 것은 위와 동일
>
> map으로 n의 값을 바꿔준 후 n 반환



```
function solution(n, control) {
  const value = {
    "w" : 1,
    "s" : -1,
    "d" : 10,
    "a" : -10
  }
  control.split('').map(e => n = n + value[e])
  return n
}
```


<br>

> 위의 경우처럼 객체를 따로 선언하지 않고 map 안에 바로 사용
```
function solution(n, control) {
  [...control].map(e => n = n + {"w" : 1, "s" : -1, "d" : 10, "a" : -10}[e])
  return n
}
```


<br>

> 함수 사용
>
> 각 문자에 해당하는 숫자로 변환하는 함수를 따로 만들어준 뒤, 원래 풀이의 solution 함수 안에서 사용해줌 



```
function solution(n, control) {
  return [...control].reduce((a, c) => stringToNum(c) + a, n)
}

const stringToNum = (n) => {
    return n === "w" ? 1 : n ==="s" ? -1 : n === "d" ? 10 : -10
}
```