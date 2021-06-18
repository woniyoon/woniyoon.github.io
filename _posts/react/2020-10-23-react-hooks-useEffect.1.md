---
layout: post
title:  "React Hooks, useEffect"
author: "Jaewon"
categories: [ react ]
---

### useRef, createRef
- current로 접근해서 조작함
- useRef().current…. & createRef().current….
<br>

### setState
- Render 메소드 안에 쓰지 않는다 

<br>
### Hooks 

<br>
### useEffect
- Hooks 사용시 라이프사이클 사용 불가 -> useEffect를 사용
- componentDidMount, componentDidUpdate, componentWillUnmount 역할을 합쳐놓음 (완전 1:1 대응은 아님)
- useEffect의 첫 번째 인수 : 함수
- useEffect의 두 번째 인수 : 배열, 바뀌는 state, useEffect를 실행하고 싶은 state
- 두 번째 인수를 비우면, 뭐가 바뀌든 신경쓰지 않음
- useEffect는 랜더링이 새로 될 때마다 실행됨

```javascript
    const [imgCoord, setImgCoord] = useState(rspCoords.바위);
    const interval = useRef();

    useEffect(()=>{     // componentDidMount, componentDidUpdate 역할
        interval.current = setInterval(changeHand, 100);
        return ()=>{    // componentWillUnmount역할
            clearInterval(interval.current);
        }
    }, [imgCoord]);
```

<br>

### 클래스 컴포넌트 라이프사이클 VS Hooks
- componentDidMount, componentDidUpdate, componentWillUnmount는 state 변경을 한 번에 처리가능
- Hooks를 이용하면 useEffect를 나눠서 처리할 수 있음 

```javascript
    componentDidMount(){
        this.setState({
            imgCoord: 3,
            score: 1,
            result: 2,
        });
    }

    useEffect(()=>{
        setImgCoord();
        setScore();
    }, [imgCoord, score]);
    useEffect(()=>{
        setResult();
    }, [result]);
```

<br>

_________________

[ZeroCho TV 유튜브 채널](https://www.youtube.com/channel/UCp-vBtwvBmDiGqjvLjChaJw)