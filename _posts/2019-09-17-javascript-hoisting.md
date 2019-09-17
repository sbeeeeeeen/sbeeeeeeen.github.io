---
# layout: post
title: "[자바스크립트] 변수 호이스팅(Variable Hoisting)"
date: 2019-09-17 09:54:24
categories: javascript hoisting
comments: true
---
  
  
  
보통 변수는 선언을 먼저 해야한다...  
근데 자바스크립트에서 `var`는 그딴 거 없다  

```javascript  
  function testFun(){
    console.log("1 ===== " + temp);
    var temp = 2;
    console.log("2 ===== " + temp);
  }
  
  testFun();
  
  > 1 ===== undefined
  > 2 ===== 2
```  
  
이러면 첫번째 로그 찍는 부분에서 아 죄송 gg요 `temp`같은 변수 없는디요ㅠㅠ 하는게 아니라 
아 `temp` 걔 `undefined`입니다~ 라고 찍힌다.... 이게 뭔진 모르지만 이미 객체 생성이 됐고 얘의 메모리 자리도 있다... 
이게 자바스크립트의 환장하는 부분인데 
이걸 호이스팅(hoisting)이라고 한다는 걸 <strike>어제 알게돼서</strike> 포스팅한다.  
  
  
    
## 호이스팅(hositing)이란!  
변수의 정의가 그 범위에 따라 선언과 할당으로 분리되는 것이다. 즉 변수가 정의되면 선언한 부분이 최상위로 올라간다는 것!  
`var`는 함수범위 안에서 유효하기땜시 지역변수면 함수 최상위, 전역변수면 전역 최상위 이런식으로 선언 및 `undefined`로 초기화까지 된다.    
  
그러니까 위의 예제는    
  
```javascript  
  function testFun(){
    var temp; //temp라는 변수의 선언이 최상위로 올라온다.  
    console.log("1 ===== " + temp); //undefined
    temp = 2;
    console.log("2 ===== " + temp); //2
  }
  
  testFun();
  
  > 1 ===== undefined
  > 2 ===== 2
```  
이렇게 되어버린다~ 참고로 `var`는 같은 변수명을 여러번 재선언해도 되기때문에(^^ 깡패가따로없음)  
  
```javascript  
  function typeTest(){}
  var typeTest;
  
  console.log(typeof typeTest);
  
  > function
```  
오류 그런 거 없다... 심지어 `var`를 나중에 선언했는데 `typeTest`는 `function`입니다^^ 라고 알려준다. 
호이스팅 과정에서 `function` 선언이 `var` 선언을 덮어씌운다고한다.. 그럼 `var`는 만년 2등 신세인가 싶지만 그건 또 아니다...환장  
  
```javascript  
  function typeTest(){}
  var typeTest = "???";
  
  console.log(typeof typeTest);
  
  > string
```  
그냥 `var`에 할당을 해주면 된다(...)  
내가 자바스크립트 개발자의 깊은 의도를 아직 파악하지 못한 걸까?....  
  
  
## let  
이래서 ES6부터 나온 것이 `let`, `const`인데 `let`은 블록범위이다!!!!  
호이스팅이 되지 않는 것은 아니고 <strong>선언은 되지만 초기화는 안한다</strong>  
  
```javascript  

{
  let temp = 2;
  console.log(temp);
}

console.log(temp);

> 2
> Uncaught ReferenceError: temp is not defined
```  
temp는 블록 안의 지역변수라 밑의 로그찍는 부분에서 에러가 뜬다! 야호  
  
```javascript  
let foo = 1;

{
  console.log(foo); 
  let foo = 2; 
}

> Uncaught ReferenceError: Cannot access 'foo' before initialization
```  
블록 범위 안에서 `foo`라는 지역변수가 있기 때문에 `let foo`가 초기화가 안됐다고 에러가 뜬다~..  
  
