---
# layout: post
title: "[자바스크립트] Set(), Map()"
date: 2019-10-07 11:59:46
categories: javascript set map
comments: true
---
  
  
  
오늘은 자바스크립트 ES6에서 추가된 `let`, `const`에 이어서 ES6에서 추가된 `Set()`과 `Map()`에 대해서 정리해보겠습니다.
  
  
  
  

## Set()    
순서와 중복이 없는 리스트이다.  
  
    
    
```javascript
  const foo = new Set();
  console.log(foo);		

  const bar = new Set([1,2,5,3,3]);
  bar.add(7);
  console.log(bar);

  > Set(5) {1, 2, 5, 3, 7}

  bar.delete(2);
  console.log(bar);

  > Set(4) {1, 5, 3, 7}

  bar.clear();
  console.log(bar);

  > Set(0) {}
```  
  
  
  - add() : 추가  
  - delete() : 삭제  
  - clear() : 값 전부 삭제 
  
  타 언어와 마찬가지로 같은 값을 계속 넣어도 한개만 존재할 뿐 오류가 나지는 않는다.  
   
  
## Map()  
위에서 정리한 `Set()`과 마찬가지로 순서와 중복이 없는데 제일 다른 점은 키-값 형태라는 것이다.  
```javascript  
  const foo = new Map();
  foo.set(1,'User');
  foo.set(2,'Master');

  const temp = foo.get(2);
  console.log(temp);
  > Master

  console.log(foo.has(1));
  > true
  foo.set(1,'Admin');

  const temp2 = foo.get(1);
  console.log(temp2);
  > Admin
  
  foo.delete(2);
  console.log(foo.get(2));
  > undefined
```  
  
- set() : 추가  
- delete() : 삭제  
- has() : 해당 키값이 존재하는지 확인  


`Set()`처럼 같은 키값 넣어도 오류 안나고 덮어씌워진다.  

