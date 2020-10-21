

---
layout: post
title:  "React props and pureComponent"
author: "Jaewon"
categories: [ react ]
---

### React props
- Parent Component에서 Child Component에게 데이터 전달 : props 사용
- Great great great parent component에서 Child component에게 데이터 전달 : context, redux, mobx 사용

<br>

### 기타
- 메소드를 클래스 밖으로 뺄지, 안에 넣어야 하나?
- 메소드 내에서 this를 사용하지 않으면 밖에 뺌 (다른 곳에서 사용할 수 있음)
- 큰 차이는 없음

<br>


### pureComponent
- 일반 Component와 달리 shouldComponentUpdate가 이미 구현되있음
- props랑 state를 얕은 비교 -> 변경된 것이 있을때는 return true; -> 변경된 것이 없을때는 return false;


<br>

_________________

[ZeroCho TV 유튜브 채널](https://www.youtube.com/channel/UCp-vBtwvBmDiGqjvLjChaJw)