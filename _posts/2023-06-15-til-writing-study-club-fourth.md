---
title:  "[글 시작 클럽 DAY 4] 깃헙 블로그 이미지와 글자 나란히 넣기"
excerpt: ""

categories:
  - TIL
tags:
  - [TIL, WritingClub, Blog]

toc: true
toc_sticky: true
 
date: 2023-06-15
last_modified_at: 2023-06-15
---

### **이미지와 텍스트 or 이미지와 이미지 한 줄에 나열하는 방법**

---

**시도해본 방법**

- span 태그 사용
- image width 작게 조절
- 추가 작성하기

**시도 결과**

- 작성하기!!

<br /><br />

### **이미지와 문단 나열하는 방법**
---
<br /><br />

이미지랑 한 문장 정도는 위의 방법으로 가능한데, 

문단이나 리스트는 위의 방법으로 하면 

이미지 라인 따로, 문단 라인 따로 

옆으로 나란히 보이지 않고 세로로 나열된다.
<br /><br />

![`style="display:inline-block`](https://postfiles.pstatic.net/MjAyMzA2MTVfMSAg/MDAxNjg2ODM1ODY1ODI3.92jjfLH49an-ZpRGcbOJygi8ukLSpwQtDKC9uhseNusg.cgM1KD_febtRv1Na9ZUPRRiY1zN1MB7hvaKQDDSJfI4g.PNG.xlzhfhqls_/스크린샷_2023-06-15_오후_10.22.29.png?type=w773)



결론적으로 해결한 방법은

이미지와 리스트를 각각 dev 태그 안에 넣고, dev 태그에 style 값을 주는 것이다.

`style="display:inline-block`

이미지의 코드는 아래 참고

```jsx
<div style="display:inline-block;vertical-align:top;">
  <img src="https://postfiles.pstatic.net/MjAyMzA2MDFfMjIx/MDAxNjg1NjI1MTQ1ODg3.xfXtRphfngU2_0KsrDwBeBrPqPtghDvqLRw3VwJOhp0g.tAhEt6f2RRpZJEDby1AIM6QXdVacc_8QWEH9KyEI3LYg.PNG.xlzhfhqls_/image.png?type=w773"  width="200" />
</div>
<div style="display:inline-block;vertical-align:top" >
    <br>
    <p> ⇒ 우선순위 정하는 단계 </p>
    <li> 사용자의 니즈 </li>
    <li> 비즈니스 방향 </li>
    <li> 기술적인 제한 </li>
    <p> → by UX 디자이너 역할 </p>
    + 실무자 모두가 포함되어 진행 (features 우선 순위 세우는 과정) 
</div>
```
<br /><br />
이미지와 텍스트 및 문단 나란히 하기는 이제 해결이 돼서 속 시원한데, 왜 이미지가 다 깨지는 걸까 😇

전에도 이런 적 있긴 했는데 시간 지나고 보면 이미지가 정상적으로 보였다.

근데 이번에는 며칠 지나도 그대로..! 

검색해본 결과 대부분은 로컬에 저장된 이미지를 그대로 업로드해서 그렇다는데 

나는 url을 입력했는걸,,,

이전에 쓴 마크다운 문법들을 봐도 같은 방법인데 이미지가 다 제대로 표시되어 있다.

의심가는 점이 몇 가지 있어서 다시 몇 가지 시도해보고

열심히 구글링 해야지..뭐... 😫

<br /><br />
> **찾을 때 검색해본 키워드!**
> 
> - How to put image and text side-by-side in HTML?
> - Place Text Next to Image in HTML

역시 영어 검색이 짱이다,, 

깃헙 블로그는 한글 포스팅이 많이 없는 것 같기도 해서 

이미지 깨지는 것도 열심히 구글링해보고 

성공하면 꼭 포스팅..!