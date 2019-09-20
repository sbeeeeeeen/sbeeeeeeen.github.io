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
  
  
...  
.....  
  
![giphy](https://user-images.githubusercontent.com/41671001/65290824-a95ea500-db8b-11e9-82a4-95493b7b03d1.gif)  
  
map이나 set같은 게 자바스크립트에도 있는지는 몰랐지만 그래도 눈에는 익으니 그렇구나 싶은데...
저 `...new Set()` 의 `...`은 무엇인가....??  
  
