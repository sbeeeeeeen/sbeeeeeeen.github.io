---
# layout: post
title: "[자바스크립트] 비구조화 할당(destructuring assignment)"
date: 2019-09-20 09:43:08
categories: javascript destructuringAssignment
comments: true
---
  
  
여느 때와 다름없이 구글링과 okky를 순회하던 나... 자바스크립트 코드를 구경하던중 이상한 걸 발견하는데...  
  
  
```javascript  
const distinctDateList = [...new Set(receive.map(o => o.item).flat().map(item => item.startDate.slice(_START_, _END_)))].map(date => new Date(date));
```  
<strike>출처를 달까했는데 못찾겠음... 찾으면 추가한다</strike>

  
  
...  
.....  
  
![giphy](https://user-images.githubusercontent.com/41671001/65290824-a95ea500-db8b-11e9-82a4-95493b7b03d1.gif)  
  
map이나 set같은 게 자바스크립트에도 있는지는 몰랐지만 그래도 눈에는 익으니 그렇구나 싶은데...
저 `...new Set()`앞의 `...`은 무엇인고하니..구글신님께서 비구조화 할당이라고 하셨다.  
  
  
## 비구조화 할당(destructuring assignment)이란 ?  
음.. 직역하자면 구조화된 객체나 배열을 쪼개서 할당해버린다는 뜻 같다. 예를 들자면  
  
```javascript  
const [a,b,...c] = ['A','B','C,','D','E'];

console.log(a);
> A

console.log(b);
> B

console.log(c);
> C, D, E
```  
보면 대략 감이 오듯이 앞의 2개 요소와 뒤의 C,D,E 요소를 ...로 분류한 것이다.  
