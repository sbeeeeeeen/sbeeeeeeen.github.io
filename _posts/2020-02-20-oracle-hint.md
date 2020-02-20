---
# layout: post
title: "[oracle] 힌트절"
date: 2020-02-20 16:19:45
categories: oracle hint
comments: true
---
    
   
<br/>
신입사원인 나. 어느 날 쿼리를 열심히 짜서 돌렸다. 너무 오래 걸린다. 이걸 어떻게 해야하나..멍..하면서 하염없이 기다렸다..^^  
결국 부장님께 SOS 요청하니 스윽 보시곤 이리저리 바꾸시더니 갑자기 SELECT 뒤에 주석을 쓰시는 것이다..
아니 보통 주석은 /* */ 인데 /*+ */ 라니 +는 갑자기 왜 쓰시는 걸까? 저게 뭔가요 여쭤보니 이것도 모르다니..하는 표정으로 
힌트를 주는 거라고 하셨다. 그게 뭔데요?...............   
  
  
  
## 힌트절 ??  
옵티마이저에게 플랜을 제공하는 거라고 한다. (옵티마이저가 뭔데?.....) 보통 최적의 플랜으로 돌려주지만 엉뚱한 실행 계획으로 돌아가는 
경우도 있는데 이 때 사용자가 강제로 실행 계획을 지시하는 것이다. 어처구니 없는 힌트 쓰면 옵티마이저가 거른다고 한다.  
  
앞서 말했듯  
```   
SELECT /*+ parallel(a 8) */
FROM TABLE a
WHERE .... 
```  
이런식으로 쓴다.  
  
    
### 종류  
여러 개가 있겠지만.. 많이 본 것들만 대략 정리.  
  
- 순서 조정을 위한 힌트  
 다수의 테이블을 조인하는 경우 사용.  
 보통 USE_NL, USE_MERGE등의 힌트와 함께 사용.  
 (순서 결정에만 힌트를 주기 때문에 USE_NL, USE_HASH를 써서 테이블 간 접근 방법도 결정함)  
 1. ORDERED  
 FROM절에 쓰여진 테이블 순서대로 조인을 수행하도록 함.  
 LEADING 힌트와 같이 사용하면 LEADING은 무시됨.  
 2. LEADING  
 정해준 순서대로 조인.  
```  
 SELECT /*+ LEADING(B C A) */ ...
 FROM  ATABLE A
          ,BTABLE B
          ,CTABLE C
 WHERE .....
```  
<br>
- 접근 방법을 결정하는 힌트  
 1. USE_HASH  
 해시 함수를 사용하여 조인(????)...  
 2. USE_NL  
 NESTED LOOPS !  하나의 테이블에서 추출된 ROW를 가지고 일일이 다른 테이블을 반복해서 조회하여 접근.  
  
<br>
- 자원 사용 결정 힌트  
 1. FULL  
 지정 테이블 풀스캔. 
 2. PARALLEL  
 병렬 처리  
 3. INDEX  
 지정 인덱스 사용  
  
<br><br>
### Reference  
[조인 순서 조정을 위한 힌트(ordered, leading)](https://blog.naver.com/light0a/140097300755){:target="_blank"}  
[접근 방법을 결정하는 힌트절? USE_NL, USE_HASH](https://programmingyoon.tistory.com/263){:target="_blank"}  
[1. Nested Loops 조인](http://wiki.gurubee.net/pages/viewpage.action?pageId=4948020){:target="_blank"}  





       
  
