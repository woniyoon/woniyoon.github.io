---
layout: post
title:  "What is Closure"
author: "Jaewon"
categories: [ javascript ]
---


- Closure is a combination of an outer function and an inner function inside. This inner function has references to variables defined in the scope of the outer function, which is called **lexical scope**. Because of the lexical environment that the returned inner function has, the variables still exist even after the outer function is called.
- It can be paired with web programming, especially when it comes to events.
- One of the benefits is that using functions like private methods is available. 
- The code attached below has an outer function, in which there is encapsulated information, such as standardFee(applicable to every tutor) and extraFeePercent of tutors. The inner function is stored in tutorService variable and returns the tutor service information if a tutor with the name given to the parameter exists. 

- 클로저는 외부함수와 그 안의 내부함수의 조합으로, **렉시컬 스코프**때문에 외부함수가 리턴하는 내부함수는 외부함수의 호출이 종료됐음에도 계속 외부함수 내부에 있는 변수들에 참조를 할 수 있다.
- 클로저는 이벤트 관련한 웹 개발에서 사용될 수 있고, 다른 프로그래밍 언어에서의 private method처럼 정보를 캡슐화하는데 사용될 수도 있다.
- 밑의 첨부된 코드는 과외 서비스에 관한 함수로, standardFee(기본비용)과 각 과외교사들 마다 다른 추가비용퍼센티지와 같은 private 정보는 외부함수의 변수에 저장되있다. 이 외부함수가 리턴하는 내부함수는 tutorService라는 변수에 저장되고, 파라미터에 주어진 이름에 해당하는 과외교사가 있다면 해당 교사가 가르치는 과목과 시간 당 과외비용을 리턴한다. 


```javascript

var tutorService = function (){
    var standardFee = 20;
    var tutors = {"Kim" : { subject: "English",
                            extraFeePercent: 0.5 }, 
                  "Park" : { subject: "Math",
                             extraFeePercent: 0.3 },
                  "Lee" : { subject: "Programming",
                             extraFeePercent: 0.4 },
                };
    
    return function(name) {
        if(tutors[name] != null) {
            return name + "'s " + tutors[name].subject + " class\n" +"tutor fee per hour : " + Number(standardFee + standardFee*tutors[name].extraFeePercent);
        } else {
            return name + " is not our tutor";
        }
    }
}();

console.log(tutorService("Kim"));   // Kim's English class
                                    // tutor fee / hour : 30
console.log(tutorService("Park"));  // Park's Math class
                                    // tutor fee / hour : 26
console.log(tutorService("Lee"));   // Lee's Programming class
                                    // tutor fee / hour : 28
console.log(tutorService("Yoon"));  // Yoon is not our tutor

```



reference source : [Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures) 



