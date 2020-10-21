

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


### pureComponent (리액트 성능 향상)
- React는 state가 변화할 때마다 랜더링이 생기는데, 성능이 악화될 수 있음
- 상황에 따라 state가 변해도 랜더링이 일어나지 않아야 하는 경우가 있는데, 이 때는 shouldComponentUpdate에서 이전 상태와 비교해서 랜더링 여부를 결정해야함
- 혹은 pureComponent를 사용하는 방법이 있음
- 일반 Component와 달리 shouldComponentUpdate가 이미 구현되있음
- props랑 state를 얕은 비교 -> 변경된 것이 있을때는 return true; -> 변경된 것이 없을때는 return false;
- 클래스 컴포넌트 사용할 때 pureComponent를 사용
- Hooks를 사용할 때는 memo를 사용

```javascript
    // pureComponent를 사용
    class Try extends PureComponent {
        render() {
            const { tryInfo } = this.props;

            ....
        }
    }

    // memo를 사용한 function Component
    const Try = memo(({tryInfo})=>{
        return (
            ...
        )
    });
    

```


<br>

_________________

[ZeroCho TV 유튜브 채널](https://www.youtube.com/channel/UCp-vBtwvBmDiGqjvLjChaJw)