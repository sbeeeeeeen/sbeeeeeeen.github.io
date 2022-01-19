---
# layout: post
title: "[Spring] 스프링 어노테이션 모음"
date: 2020-10-21 11:37:21
categories: spring
comments: true
---
    
   
<br/>
내가 보려고 정리해놓는 어노테이션 모음  
오랜만에 깃헙 들어오는데 뭔가 좀 바뀐것같네...    
  
  
  
-- @Getter, @Setter  
말그대로 getter/setter

-- @Data  
찾아보니 여러 어노테이션의 조합이라고하는데 ( 출처 : [롬복(Lombok) 애노테이션 사용하기](https://siyoon210.tistory.com/24){:target="_blank"} )

-- @EqualsAndHashCode  
equals, HashCode(==) 생성    

-- @NoArgsConstructor  
기본생성자 생성

-- @AllArgsConstructor  
모든 필드값 포함 생성자 생성

-- @Slf4j  
log.debug ~ info ~ 

-- @JsonProperty    
Jackson 라이브러리(JSON 데이터구조 처리)에서 제공하는 어노테이션인데..    
결함건 수정하다가 변수명 첫글자가 한글자인 케이스는 값이 들어오지 않는 걸 알게됐다 (예:sCustNm)    
-잠깐 잡소리-    
옛날 소스 보니 앞에 s를 붙여놓은 케이스가 많아서 왜이렇게햇을까 궁금해서 구글링해봤다    
헝가리안 표기법이라는게 있단다. 데이터 변수(s의 경우엔 String이겠지) 한글자를 앞에 붙이는 거라고 하는데
지금은 사용하지 않는다고한다. 애초에 변수 타입 바꾸면 변수명도 바꿔야되는데 불편하다;;    
아무튼 json 일때 매핑명을 따로 정해주는것~~ req DTO json 으로 받으니 거기에 한글자인것들에 어노테이션 달아놨다.참고로 일부에만 어노테이션을 붙이면 붙인 변수가 먼저 출력이 된다고함! 순서를 보장해야한다면 다 붙여버리자
