---
layout: post
title:  "addEventListener with ‘getElementById()’"
author: "Jaewon"
comments: false
categories: [ javascript ]
---

```html
<script type="text/javascript">
	window.onload = function(event){
		
		var btn1 = document.getElementById("btn1");
		
		// btn1 onclick event definition
		btn1.addEventListener("click", function(){
            ...
		});
		
		
		// btn2 onclick event definition
		btn2.addEventListener("click", function(event){
            ...
		});
	}
</script>

....

<table>
	<tr>
		<td><input type="text" id="text1" value="abcdefghi123456" /></td>
    	<td><input type="button" id="btn1" value="확인" /></td>
	</tr>
	<tr>
    	<td><input type="text" id="text2" /></td>
		<td><input type="button" id="btn2" value="다시"/></td>
	</tr>
</table>

```

&nbsp;


- Creating HTML DOM variable object is done with 'getElementById('element_id')', but also without it. We can access HTML elements by their id. The code above is the example. 'btn1' variable is assigned by 'document.getElementById('btn1');', 'btn2', however, isn't using the method.

- That is because Internet Explorer made window object have these HTML elements as its own properties under their name. Despite having shorter code, it's more safe to use getElementById to avoid misassigning to a global variable with a clashing name and occuring errors.

- Javascript 코드에서 HTML 태그에 연결되는 변수를 생성할 때 'getElementById('element_id')'를 이용한다. 그러나 document의 메소드없이 해당 HTML 태그의 id를 이용해 접근할 수도 있다. 위 코드의 btn1과 btn2에 각각 EventListener를 각각 다른 방법으로 추가하고 있다. btn2는 btn1처럼 getElementById를 사용하지 않고 btn2이라는 버튼의 id를 이용해 바로 EventListener를 추가하고 있다.

- Internet Explorer가 이 HTML 요소들을 window object의 속성들인것처럼 추가되게끔 만들었고, 다른 웹브라우저에서도 이를 허용한다. 간결한 코드라는 장점이 있지만, 변수명이 겹치면서 일어날 수 있는 에러가 발생할 수 있다. getElementById()를 통해 HTML element 변수 만들어주는 것이 좋은 관습이라고 한다.

&nbsp;

_________________

reference source : [https://stackoverflow.com/questions/3434278/do-dom-tree-elements-with-ids-become-global-variables/3434388#3434388](https://stackoverflow.com/questions/3434278/do-dom-tree-elements-with-ids-become-global-variables/3434388#3434388) 
