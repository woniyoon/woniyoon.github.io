

---
layout: post
title:  "React와 Webpack"
author: "Jaewon"
categories: [ react ]
---

### WEBPACK

- dependencies 속성에 값을 많이 넣으면 build가 오래 걸림 -> 최소한으로 깔아주는 게 좋음 (devDependencies 이용)
- Webpack = 설정의 연속
- plugin의 모음이 preset
- webpack의 메인 : entry, module(=Loaders), output, plugins(실무 코드에는 보통  10개 정도 들어있음)
- 코드를 바꿀 때마다 webpack build하기 번거로움
    ->  자동 build 설정하는 법
     1. Npm I -D react-hot-loader 설치
     2. Npm I -D webpack-dev-server 설치 ( webpack.config.js를 읽어서 build & 서버에 실행시켜줌)
     3. scripts에 “dev”: “webpack-dev-server —hot” 추가 
     4. client.jsx에서 hot (react-hot-loader/root) 불러와서 적용
     5. webpack.config.js에 babel options -> plugins에 ‘react-hot-loader/babel’ 추가
- Webpack dev server 는 output 설정된 app.js대로가 아니라 다른 방식으로 실행  

<br>

### React

- 의미없는 div태그 대신 Fragment를 사용할 수 있다

```javascript
    return (
        <>
            <p>비어있는 태그를 사용</p>
        </>
    );
```
- Form 태그 안에 input 사용시, 1. value와 onChange를 같이 사용 2. defaultValue 속성을 사용해줘야 에러메시지 안 나옴


<br>

_________________

[ZeroCho TV 유튜브 채널](https://www.youtube.com/channel/UCp-vBtwvBmDiGqjvLjChaJw)