

---
layout: post
title:  "Webpack과 Babel"
author: "Jaewon"
categories: [ react ]
---

### WEBPACK

-  페이스북 컴포넌트 수 2만개 -> 컴포넌트가 많아질수록 유지보수가 힘듦 -> 모든 컴포넌트를 합쳐서 하나의 js로 만들어주는 것 (바벨 적용도 가능, console.log를 제거할 수도 있음) 
- 수 백에서 수 천개로 합쳐지는 js파일을 하나로 합쳐줌 
- WEBPACK을 알려면 node.js를 알아야함
- Node.js는 자바스크립트 실행기일뿐, 서버에 한정지으면 X
- 실제 서비스할 때는 webpack이 필요없고, 개발용으로 사용하기 때문에 npm I -D web pack webpack-cli 명령어를 사용
- 모듈 시스템이 있기 때문에 예전처럼 사용하지 않는 모듈마저 다 가져올 필요가 없어지고, 필요한 것만 가져와서 사용함 
- node의 모듈 시스템을 이용해서 불러올 수 있기 때문에 더 이상 <script></script>가 필요없음
- <script src=“./dist/app.js></script>만 남음
- 여러가지 모듈을 가져와서 쓰려면 ./dist/app.js에 넣어줘야 HTML이 인식할 수 있음-> webpack이 이 모든걸 합쳐줌
- 즉, client.jsx와 WordRelay.jsx를 app.js에 넣어줘야함 -> 이를 위해 webpack.config.js를 사용함
<br>
<br>

```javascript
// webpack.config.js

module.exports = {
 	name: “아무 이름”,
	mode: “development”, // production 실서비스용
	devtool: “eval”, //빠르게?
	resolve:  {
		extensions: [“.js”, “.jsx”]
	},
	entry: {
		app: [“./client.jsx”, ”./WordRelay.jsx”], // 그러나 client.jsx가 WordRelay.jsx를 import하고 있기 때문에 client.jsx만 써도 되고, 위에 resolve프로퍼티 때문에 확장자를 빼고 client만 넣어도 됨
	},
	module: {
		rules: [{
			test: /\.jsx?/, // jsx확장자 파일에 룰을 적용하겠다
			loader: “babel-loader”,
			options: {
				presets: [“@babel/preset-env“, “@babel/preset-react”],
			},
		}],
	},
	output: {
		path: path.join(__dirname, “dist”),	// 현재 폴더 안에 있는 dist (__dirname : 현재폴더)
		filename: “app.js”
	},
};
```

<br>
<br>

### BABEL

- 웹팩 설정 후, 바벨 설정해줌

```
npm i -D @babel/core : 바벨도 개발자용, 기본적 바벨, 최신 문법 바꿔줌
npm i -D @babel/preset-env : 브라우저의 문법을 환경에 맞게, 브라우저에 맞게 알아서 변환해줌
npm i -D @babel/preset-react : jsx같은걸 지원 
npm i babel-loader : 바벨 & 웹팩을 연결해줌
```

- webpack 명령어 치면 app.js를 만들어줌 
- Command not found : 명령어 등록 필요
    1. script에 넣거나 (package.json에 scripts에 넣기)
    2. npx webpack?

<br>

_________________

[ZeroCho TV 유튜브 채널](https://www.youtube.com/channel/UCp-vBtwvBmDiGqjvLjChaJw)