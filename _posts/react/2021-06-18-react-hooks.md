---
layout: post
title:  "React Hooks"
author: "Jaewon"
categories: [ react ]
---

### Basic Hooks 
- useState
- useEffect
- useContext
<br>

### Additional Hooks
- useReducer
- useCallback
- useMemo
- useRef
- useImperativeHandle
- useLayoutEffect

<br>
### Custom Hooks 

<br>
### useState
- useState의 인자로 함수를 넣으면, 리액트가 이 함수를 호출함
- 일반 함수로 전달하면, 랜더링 될 때마다 실행이 됨
- 이를 방지하려면 익명함수를 이용해 함수 reference를 전달 -> 함수가 한 번만 실행됨

```javascript
    function mountState(initialState) {
    var hook = mountWorkInProgressHook();

    if (typeof initialState === 'function') { // this is the line of code what we are looking 
        initialState = initialState();
    }

    hook.memoizedState = hook.baseState = initialState;
    var queue = hook.queue = {
        last: null,
        dispatch: null,
        lastRenderedReducer: basicStateReducer,
        lastRenderedState: initialState
    };
    var dispatch = queue.dispatch = dispatchAction.bind(null, currentlyRenderingFiber$1, queue);
    return [hook.memoizedState, dispatch];
}
```
<br/>
- State를 업데이트 하는 방법
- 1.setCount에 직접적으로 값을 주거나 2.setCount에 화살표 함수를 이용

```javascript
import React, { useEffect, useState } from 'react';

const HelloComponent = (props) => {
    const [count, setCount] = useState(0);

    return (
        <div>
            <span>{count}</span>
            <button onClick={() => setCount(count + 1)}>Increment</button>
            <button onClick={() => setCount((oldValue) => {
                const value = oldValue - 1;
                return value;
            })}>Decrement</button>
        </div>
    )
}

export default HelloComponent
```

<br>

### useEffect 유스케이스
1. 컴포넌트 최초 랜더링할 때 이용
2. 컴포넌트가 언마운트 될 때
3. state 변동시 실행되어야 하거나 처리해야하는 코드 사용시

<br>

### useEffect 유스케이스
1. 컴포넌트 최초 랜더링할 때 이용
2. 컴포넌트가 언마운트 될 때
3. state 변동시 실행되어야 하거나 처리해야하는 코드 사용시

<br>
### useContext
- props drilling: 상위 컴포넌트에서 하위 컴포넌트로 props을 간접적으로(다른 컴포넌트들을 통해) 전달하는 것
- 상위 컴포넌트에서 바로 타겟 컴포넌트로 전달하기 위해 context API를 사용

```javascript
import React, { createContext, useContext, useEffect, useState } from 'react';

const MyContext = createContext();

const ParentComponent = (props) => {

    return <MyContext.Provider value={{ hello: 'Hello World' }}>
        <ChildOne />
    </MyContext.Provider>
}

const ChildOne = () => {
    return <ChildTwo />
}

const ChildTwo = () => {
    return <ChildThree />
}

const ChildThree = () => {
    const contextData = useContext(MyContext);  // ChildOne, ChildTwo를 거치지 않고
                                                // 바로 ChildThree에게 전달
    return <div>{contextData.hello}</div>
}

export default ParentComponent
```
<br/>


### useReducer
- useState를 대체할 수 있는 hooks
- 좀 더 복잡한 state logic을 구현할 때 사용
- const [state, dispatch] = useReducer(reducer, initialArg, init);

### useCallback
- map을 사용하여 랜더된 자식 컴포넌트는, 맵핑된 데이터가 변동될 때마다 다시 랜더링이 다시 됨
- 만약 자식 컴포넌트가 클릭 이벤트가 있다면 이벤트 함수 참조도 계속 바뀜
- 이 때, useCallback을 이용!

```javascript
import React, { useCallback, useState } from 'react';

const ParentComponent = () => { 
    return <React.Fragment>
        {(new Array(10).fill(1).map((elem) => <ChildComponent />)   )}
    </React.Fragment>
}

const ChildComponent = () => {
    const memorizedFun = useCallback(() => {
        console.log('Hello World')
    }, [])
    return <div onClick={() => memorizedFun()}>Child Component</div>
}

export default ParentComponent
```

<br/>

### useRef
- 돔이나 자식 컴포넌트의 prop값들에 접근할 때 사용?



_________________

[Fundamentals of React Hooks in 7 minutes](https://javascript.plainenglish.io/fundamentals-of-react-hooks-in-6-minutes-by-bytecode-pandit-656e5a38f57)
[How to avoid the useState function parameter (to get initial values) from being executed on every render?](https://stackoverflow.com/questions/58096155/how-to-avoid-the-usestate-function-parameter-to-get-initial-values-from-being)
