---
# layout: post
title: "[Java] Wrapper 클래스"
date: 2020-02-18 11:32:02
categories: java wrapper
comments: true
---
    
   
  
오랜만에 자바 코딩하는데 ㅋㅋㅋㅋㅋㅋㅋㅋㅋ 아 다시 생각해도 너무 웃기네  
NUMBER(n,n) 타입 컬럼에 자꾸 0.0이 insert.가 됐다...  
난 null을 넣고싶은데.... VO에 set을 아무것도 안했는데... 흠 뭐가 문제일까...     
    
  
![unnamed](https://user-images.githubusercontent.com/41671001/74699039-f6ca6580-5242-11ea-90a1-f091c6489620.jpg)  
계속 이 표정으로 n시간을 모니터만 쳐다보다가....  
(사실.. 흥미가 0이었음)    
   
![캡처](https://user-images.githubusercontent.com/41671001/74699384-e36bca00-5243-11ea-8b42-8581e073fa46.JPG)  
문득 왜.. double만 색깔이 다르지??.........싶었다...  
와 진짜 바보인가... 내가 이걸 까먹다니.ㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎ  
복습합니다.  
  
  
### Wrapper 클래스  
![Wrapper-Class](https://user-images.githubusercontent.com/41671001/74713070-22f9dc80-526b-11ea-860a-6385c205d520.png)  
[출처](https://www.geeksforgeeks.org/wrapper-classes-java/){: target="_blank" }  
  
갑자기.. 왜 하필 래퍼클래스라고 칭하는지 궁금해서 한 5초 찾아봤는데 말 그대로 원시 데이터(int, double ... )를 
래퍼 클래스 객체(오브젝트)로 래핑..하기 때문이란다.. 너무 직관적이라 할 말이 없다...  
위의 표를 보면 알겠지만 따로 외울 필요도 없다 비슷하니까 대충 때려맞추면 생각이 날 것이다  
각설하고 몇가지 복습하자면  
  
1. java.util 패키지 클래스는 객체만 처리하기 때문에 원시데이터를 쓸 수 없다.  
예를 들자면..  
```  
List<int> tempList = new ArrayList<int>();  
Map<int, long> tempMap = new HashMap<int, long>();  
```
당연히(...) 안된다.  
``` 
List<Integer> tempList = new ArrayList<Integer>();  
```  
편ㅡ안....  
   
2. 오토박싱 언박싱  
이걸 칭하는 말이 왜 있는지는 모르겠는데.. 뭐 아무튼  
  
- 오토박싱  
원시 데이터 ------------------> 해당 래퍼 클래스 객체  
ex) int        ------------------>  Integer  
  
- 언박싱  
래퍼 클래스 객체 -----------------------> 원시 데이터  
ex ) Integer        ------------------------>   int  
  

 
