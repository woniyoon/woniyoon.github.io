---
layout: post
title:  "replaceAll() in JS"
author: "Jaewon"
categories: [ javascript ]
---


```javascript
// Elements stored in variables
var btnOK = document.getElementById("btnOK");
var inputText = document.getElementById("inputText");

//  every hyphen in sInputText will be replaced with empty space
//  , when btnOK is clicked
btnOK.addEventListener("click", function(event){
	var sInputText = inputText.value;

	document.getElementById("result").innerHTML = sInputText.replace(/-/g, "");
});

```


- **str.replace(regexp|substr, newSubstr|function)**
- Javascript only provides **replace()** but no **replaceAll()**
- **/-/g** from the example code is a regex expression, of which 'g' means globally  <br/><br/>

- 자바스크립트는 replaceAll() 메소드가 없으므로, replace() 메소드에 정규표현식을 이용해 대체할 수 있다.<br/><br/>

```javascript
str.replace(/any_chars/i, "new_chars")
// replace any_chars with new_chars ignoring case
// 대문자/소문자 구별없이 any_chars를 new_chars로 교체
```

```javascript
str.replace(/any_chars/gi, "new_chars")
// replace all of any_chars with new_chars ignoring case 
// 대문자/소문자 구별없이 str안의 모든 any_chars를 new_chars로 교체
```

```javascript
str.replace(/any_chars/, function(x){ return x.toUpperCase(); })
// uppercase any_chars in str 
// str안의 any_chars를 대문자로 교체
```





