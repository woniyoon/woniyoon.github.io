---
layout: post
title:  "React Hooks 관련 공부"
author: "Jaewon"
categories: [ react ]
---

### REACT HOOKS

- 클래스 컴포넌트 대신에 Hooks를 이용해 함수 컴포넌트 사용 가능
- React.use … 로 시작하는게 Hooks 
    (useState, useRef(DOM에 접근시 React.useRef().current를 이용해야함),…)
- 코드가 더 짧아짐 
- state가 바뀔 시, 함수 컴포넌트가 처음부터 다시 실행되기 때문에 최적화 문제가 생길 수 있다 
<br>
```javascript 
class Page extends React.Component {
    state = { 
          value: 0
    }
}
```
<br>
```javascript
const Page = () => {
    const [value, setValue] = React.useState(0);
}
```

<br>

_________________

[ZeroCho TV 유튜브 채널](https://www.youtube.com/channel/UCp-vBtwvBmDiGqjvLjChaJw)