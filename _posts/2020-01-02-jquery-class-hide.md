---
# layout: post
title: "[jQuery] 같은 클래스를 가진 여러 개체중 특정 개체만 hide하기"
date: 2020-01-02 10:43:34
categories: html jQuery
comments: true
---
  
  
```
<div class="box">box1</div>
<div class="box">box2</div>
<div class="box">       </div>
<div class="box">box4</div>
```
  
난 box 클래스를 갖고있는 div중에서 값이 없는(빈값인) div만 숨기고싶다.....면 !
  
  
  
```
$('div[class=box]').each(function(){
	if(!$.trim($(this).text()))
		$(this).hide();
});
```  
  

아 이렇게 쉬운데....  
제이쿼리는 잘 모르겠고,, 프로젝트 시간은 짧고,,,  
어버버대느라 시간 좀 잡아먹은듯?  
또 까먹을테니 기록용으로 ......   
  

