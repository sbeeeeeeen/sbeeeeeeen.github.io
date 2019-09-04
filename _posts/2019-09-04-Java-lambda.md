---
title: "[Java] 람다식"
date: 2019-09-04 10:29:23
categories: java lambda
---
  
  자바8부터 적용된 람다식에 대해 알아보자.  
    
  
## 람다식?  
메서드를 하나의 식으로 표현한 것. 자바에는 함수라는 개념이 없지만 람다식을 이용하여 함수형 프로그래밍을 할 수 있다. 즉 객체 생성 없이 메서드를 쓸 수 있기 때문에 익명 메서드라고도 한다.  
  
  
## 사용법  
 
원래 메서드를 사용한다고 하면  
> method(매개변수){  
> nbsp;nbsp;nbsp;nbsp;실행코드;  
> }  
  
이런식으로 작성하는데, 이걸  
> (매개변수) -> {실행코드;}  
  이렇게 간단하게(^^) 할 수 있다.. 말은 참 쉽죠 처음 봤을 땐 이건 뭔가 싶었다..  
  
-예제  
```java
@FunctionalInterface
public interface LambdaExamAddInf {
	int add(int a, int b);
}
```  
  
그냥 인터페이스에 `int` 매개변수 두개를 받아 `int`를 리턴하는 메서드 하나를 만들었다. 람다식은 함수형 인터페이스, 즉 하나의 추상 메서드만 선언된 인터페이스를 구현하는 방식이기 때문에 무조건 메서드는 하나여야한다. (아니면 오류남) 
위의 `@FunctionalInterface` 어노테이션이 이거 함수형 인터페이스라 1메서드임이란 뜻  
  
어쨌든 클래스를 만들어서 이 인터페이스를 써보겠다~ 생각해보면 우리는  
```java  
public class LambdaSample{
  public static void main(String[] args) {
    LambdaExamAddInf lambdaInf = new LambdaExamAddInf() {
      @Override
      public int add(int a, int b){
        return a+b;
      }
    }
    
    int result = lambdaInf.add(5,7);
    System.out.print(result);
  }
}
```  
  
이런 식으로 쓸 수 있는데, 이것을 람다식으로 표현하면  
  
```java  
public class LambdaSample{
  public static void main(String[] args) {
    LambdaExamAddInf lambdaInf = (int a, int b)->{return a+b;};
		
		int result = lambdaInf.add(5, 7);
		System.out.println(result);
  }
}
```  
이렇게 간소화 할 수 있다....  

