---
title: "[Java] 람다식"
date: 2019-09-04 10:29:23
categories: java lambda
---
  
  자바8부터 적용된 람다식에 대해 알아보자.  
    
  
## 람다식?  
메서드를 하나의 식으로 표현한 것. 자바에는 함수라는 개념이 없지만 람다식을 이용하여 함수형 프로그래밍을 할 수 있다. 즉 익명 함수를 정의하여 메서드를 쓸 수 있기 때문에 익명 메서드라고도 한다.  
  
  
## 사용법  
 
원래 메서드를 만들 때   
> method(매개변수){  
> &nbsp; &nbsp; &nbsp; &nbsp; 실행코드;  
> }  
  
이런식으로 작성하고 객체 생성을 통해서 메서드를 사용한다. 클래스에 종속적이다.  
하지만 익명 함수는  
  
> (매개변수) -> {실행코드;}  
  
이렇게 간단하게(^^) 구현할 수 있다.. 말은 참 쉽죠 처음 봤을 땐 이건 뭔가 싶었다..  
  
-예제  
```java
@FunctionalInterface
public interface LambdaExamAddInf {
	int add(int a, int b);
}
```  
  
인터페이스에 `int` 매개변수 두개를 받아 `int`를 리턴하는 메서드 하나를 만들었다. 람다식은 함수형 인터페이스, 즉 하나의 추상 메서드만 선언된 인터페이스를 구현하는 방식이기 때문에 무조건 1인터페이스엔 1메서드다.  
위의 `@FunctionalInterface` 어노테이션은.. 그냥 쓰는 거다.. 친구들아.. 이 인터페이스는 람다식을 쓴단다.. 알려주는건데
정작 컴파일러는 인터페이스 구조로 함수형 인터페이스 여부를 판단하기때문에 필요가 없다. 선택적인 어노테이션이라 안써도 된다.   
  
  
어쨌든 클래스를 만들어서 이 인터페이스를 구현해보겠소한다면    
```java  
public class LambdaSample{
  public static void main(String[] args) {
    LambdaExamAddInf lambdaInf = new LambdaExamAddInf() {
      @Override
      public int add(int a, int b){
        return a+b;
      }
    };
    
    int result = lambdaInf.add(5,7);
    System.out.print(result);
  }
}
```  
  
이런 식으로 쓸 수 있는데, 이것을 람다식으로 표현해보면  
  
```java  
public class LambdaSample{
  public static void main(String[] args) {
    LambdaExamAddInf lambdaInf = (int a, int b)->{return a+b;};
    int result = lambdaInf.add(5, 7);
    System.out.println(result);
  }
}
```  
이렇게 간소화 할 수 있다.... 근데 여기서 생략이 더 가능하다..^^  
  
- 매개변수의 자료형 타입이 하나이면 생략 가능(컴파일러가 찾아준다)  
> LambdaExamAddInf lambdaInf = (a, b)->{return a+b;};  
- 매개변수가 한개라면 소괄호 생략 가능  
> LambdaExamAddInf lambdaInf = a->{return a+b;};  
- 구현한게 return문 하나밖에 없으면 return도 생략 가능..  
> LambdaExamAddInf lambdaInf = (a, b)->a+b;  
  
끝이다.. 이 외에 좀 더 주의사항이 있다면 `break`, `continue`같은 람다 바디 밖으로 탈출하는 키워드는 사용 불가능하다는 것 정도다..
  
예를 좀 더 들기 위해서 함수형 인터페이스인 `Runnable`을 이용해서 쓰레드를 구현해보면  
  
예제1.  
```java
Runnable th = () -> System.out.println("test"); //매개변수가 없어도 소괄호는 써야한다.
th.run();
```  
  
가 되시겠다.  
  
또 많이 쓰는 `Comparator`를 써보면  
  
예제2.  
```java
    List<Integer> list = new ArrayList<Integer>();
    list.add(3);
    list.add(1);
    list.add(5);

    //람다식 적용 X
    Collections.sort(list, new Comparator<Integer>() {
	@Override
	public int compare(Integer x, Integer y) {
		return Integer.compare(x, y);
	}
    });

    //람다식 적용 O
    Collections.sort(list, (x,y)->Integer.compare(x, y));

    System.out.println(list);
```
  
이런 식으로 적용할 수 있다.  
  
  
참고로.. 자바8에서 java.util.function package에 추가된 함수형 인터페이스가 있다...몇개만 살펴보자면<strike>(이제 그만..)</strike><br>
### java.util.function  
- Function<T,R>  
  
T를 매개변수로 R을 리턴.  
  
```java
Function<Integer, Boolean> function = new Function<Integer, Boolean>() {
	@Override
	public Boolean apply(Integer t) {
		return t==1?true:false;
	}
};
System.out.println(function.apply(1));

Function<Integer, Boolean> functionLambda = t->t==1?true:false;
System.out.println(functionLambda.apply(1));
```  
  
  
- Consumer  
  
void... 단순 처리용...  
  
```java
Consumer<String> consumer = new Consumer<String>() {
	@Override
	public void accept(String t) {
		System.out.println(t);
	}
};
consumer.accept("자바");
		
Consumer<String> consumerLambda = t -> System.out.println(t);
consumerLambda.accept("자바");
```  
  
  
- Predicate \<T>\  
  
T를 받아 boolean 리턴..  
  
```java
Predicate<Integer> predicate = new Predicate<Integer>() {
	@Override
	public boolean test(Integer t) {
		return t%2==0;
	}
};
System.out.println(predicate.test(4));

Predicate<Integer> predicateLambda = t -> t%2==0;
System.out.println(predicateLambda.test(4));
```  
  
  
- Supplier<pre><T></pre>
  
T를 리턴... 매개변수 없음.  
  
```java
Supplier<Integer> supplier = new Supplier<Integer>() {
	@Override
	public Integer get() {
		return 1;
	}
};
System.out.println(supplier.get());

Supplier<Integer> supplierLambda = ()->1;
System.out.println(supplierLambda.get());
```  
  
