## JAVA

#### 1. 자바의 장단점
장점 : 플렛폼에 상관없이 VM만 있다면 실행이 가능하다.
단점 : VM위에서 돌아가기 때문에 VM이 있어야하며 이에 따라 성능저하가 있다.
#### 2. OOP의 특징 4가지

1) 추상화   
객체의 공통적인 특징을 파악해 하나의 개념(클래스)으로 다루는 것.   
2) 상속(일반화)  
상위 개념을 하위 개념이 물려받아 재사용성을 높인다.  
3) 다형성    
다양한 형태로 표현이 가능한 구조를 의미한다. 서로 다른 클래스의 객체가 같은 입력을 받았을 때 각자의 방식으로 동작하는 것.   
4) 정보 은닉   
캡슐화로 데이터와 데이터를 다루는 법을 묶고, 내부 정보를 밖에서 조회/변경할 수 없게 한다.   


#### 3. SOLID에 대해 설명

> 객체지향개발의 5대 원리

객체지향 개발의 디자인 원리들을 사용하면 좀 더 유지보수하기 쉽고, 유연하고, 확장이 쉬운 소프트웨어를 만들 수 있습니다. 

* 5가지 원리의 핵심 내용
  1. 단일 책임 원칙 (Single Responsibility Principle)
     * **모든 클래스는 각각 하나의 책임만 가져야 한다.** 클래스는 그 책임을 완전히 캡슐화 해야 한다. 
  2. 개방 - 폐쇄 원칙 (Open Closed Principle)
     * 확장에는 열려 있고 수정에는 닫혀있는, **기존의 코드를 변경하지 않으면서 기능을 추가할 수 있도록 설계** 가 되어야 한다는 원칙.
  3. 리스코프 치환 원칙 (Liskov Substitution Principle)
     * **자식 클래스는 언제나 자신의 부모 클래스를 대체 할 수 있다는 원칙.** 
     * 자식 클래스는 부모 클래스의 책임을 무시하거나 재정의 하지 않고 확장만 수행하도록 해야 LSP 를 만족한다. 
  4. 인터페이스 분리 원칙 (Interface Segregation Principle)
     * 한 클래스는 자신이 사용하지 않는 인터페이스는 구현하지 말아야 한다.
     * **하나의 일반적인 인터페이스보다는 여러개의 구체적인 인터페이스가 낫다.**
  5. 의존 역전 원칙 (Dependency Inversion Principle)
     * 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것보다는 변화하기 어려운 것, 거의 변화가 없는 것에 의존하라는 것.
     * 말이 너무 추상적이라 정리하자면, **구체적인 클래스보다 인터페이스나 추상클래스와 관계를 맺으라는 것.** 

#### 4. GC에 대해서 설명   
GC는 Garbage Collection으로, 힙 영역에서 메모리 부족 현상을 해결하기 위해 쓰이지 않는 객체를 해제하는 작업이다.   
(1)사용하는 객체를 **mark**하고 (2) mark되지 않는 객체를 **제거**하고 (3) full GC의 경우 제거함으로써 생기는 hole을 **압축**(Compact)한다.   
모든 종류의 GC에서 STW가 발생한다.
* Miner GC : 사용되지 않는 객체는 제거되고, 살아남은 객체만 survivor 1, 2 영역으로 이동. 오래 살아남은 객체는 old 영역으로 이동한다.   
* Major GC(full GC) : 단편화를 줄이기 위해 hole을 모으는 과정에서 STW가 발생한다.    



#### 5. STW란

GC을 실행하기 위해 JVM이 애플리케이션 실행을 멈추는 것.

stop-the-world가 발생하면 GC를 실행하는 쓰레드를 제외한 나머지 쓰레드는 모두 작업을 멈춘다. 

GC 작업을 완료한 이후에야 중단했던 작업을 다시 시작한다.

#### 6. Objects의 기본 메소드
- equals : 동등성 검사
- hashcode : 해쉬벨류 생성
- toString : 문자열로 만듬

#### 7. String, StringBuilder, StringBuffer의 차이    
String으로 생성된 문자열은 변경할 수 없다.   
StringBuilder와 StringBuffer는 char로 문자열을 쌓은 후, 필요할 때마다 toString으로 문자열 객체를 만든다.   
StringBuilder는 동기화를 지원하지 않는다는 차이가 있다.    

#### 8. '=='와 equals의 차이
#### 9. String str = new String()과 String str = ""의 차이

> String pool에 저장이 되느냐 그냥 heap에 따로 저장되느냐의 차이.

String을 생성하는 두가지 방식

1. new 연산자를 이용한 방식
2. 리터럴을 이용한 방식

Java의 Heap에는 `String Pool` 이라는 특별한 영역에서 String 객체들을 관리합니다. 이 String Pool의 실체는 `HashMap`입니다. 다음 코드와 같이 문자열 리터럴을 사용하여 String 객체를 생성하면 `String Pool`에 기존에 같은 값을 가지는 String 객체가 있는지 검사하고 있으면 그 객체의 참조값을, 없으면 String Pool에 새로 String 객체를 생성하고 그 참조값을 리턴합니다.

그러므로 아래와 같은 결과를 확인할 수 있습니다. new 를 통한 객체 생성시에는 string pool에 생성되지 않고 따로 생성됩니다. 

~~~java
String a = "aaa";
String b = "aaa";
String c = new String("aaa");
String d = new String("aaa");

System.out.println(a==b); //true
System.out.println(a==c);//false
System.out.println(a==d);//false
System.out.println(c==d);//false
System.out.println(a.equals(b));//true
System.out.println(a.equals(c));//true
System.out.println(c.equals(d));//true
~~~

![image](https://user-images.githubusercontent.com/36303777/96821049-28df3780-1462-11eb-9cc3-389229ad0980.png)



#### 10. 자바의 접근 제어자에 대해 설명
- private : 외부에서 접근 불가
- package private : 패키지 외부에서 접근 불가
- protected : 하위 클래스에서만 접근 가능
- public : 외부에서 접근 가능

#### 11. 오버라이딩과 오버로딩에 대해 설명  

오버라이딩: 부모 클래스의 메소드를 자식 클래스에서 재정의 하는 것.
오버로딩: 클래스에서 같은 이름의 메소드를 다른 인자를 받게 하여 여러 개 정의할 수 있는 것.

#### 12. Generic이란?

제네릭은 다양한 타입의 객체들을 다루는 메서드나 컬렉션 클래스에 컴파일 시의 타입 체크를 해주는 기능입니다.

즉, **클래스 내부에서 사용할 데이터 타입을 나중에 인스턴스를 생성할 때 확정하는 것**을 **제네릭**이라 합니다.

제네릭의 장점은 

1. 컴파일 시 강한 타입 체크를 할 수 있다.
   - 실행시 타입 에러가 나는 것보다 컴파일 시에 미리 타입을 강하게 체크해서 에러를 사전에 방지
2. 타입 변환(casting)을 제거한다.
   - 비제네릭 코드는 불필요하게 타입 변환을 하기 때문에 프로그램 성능에 악영향을 미친다.

> #### 와일드카드란, 
>
> 제네릭 클래스의 객체를 메소드의 매개변수로 받을 때, 그 객체의 타입 변수를 제한하는 것을 말한다.
>
> #### 와일드 카드<?>의 제한 종류
>
> - **<? extends T>** 와일드 카드의 상한 제한(upper bound) - T와 그 자손들을 구현한 객체들만 매개변수로 가능
> - **<? super T>** 와일드 카드의 하한 제한(lower bound) -T와 그 조상들을 구현한 객체들만 매개변수로 가능
> - **<?>** 제한 없음

#### 13. 인터페이스와 추상클래스의 차이
- 인터페이스는 다중 확장 가능, 추상 클래스는 불가
- 인터페이스의 필드값는 static final이지만 추상클래스는 non-static, non-final 필드 가능

#### 14. 자바 멀티쓰레드에서 동기화 방법   

1) syncronized 키워드 사용    
메소드 정의부 옆이나, 블록을 만들어서 구현할 수 있다.  
클래스 기반 lock이므로 한 클래스에 syncronized 키워드가 붙은 메소드가 여러개라면,  
그중 한개라도 다른 스레드가 사용하고 있을 경우 나머지 메소드(syncronized가 붙은)도 실행할 수 없다.   

2) lock object 구현   
직접 lock 역할을 하는 object를 구현할 수 있다.    

#### 15. 자바8 변경사항

- **람다 표현식 (Lambda expression):** 함수형 프로그래밍이 가능하게 됨
- **스트림 API (Stream API):** 데이터를 추상화하여 다룰 수 있게 됨
- **java.time 패키지:** 더 직관적이고 개선된 Date, Time API를 제공
- **나즈혼 (Nashorn):** 자바스크립트의 새로운 엔진을 도입

#### 16. static 이란?
- 메모리에 단 한번만 올라가는 데이터

#### 17. 동적바인딩 설명

#### 18. 업캐스팅

#### 19. primary type / non-primary type 차이 설명

#### 20. JVM이란?

#### 21. 직렬화 설명

------

#### 22. Dynamic typing과 Static Typing의 차이

#### 23. 자바의 final 키워드

#### 24. 제네릭 사용하는 이유

#### 25. 다형성 설명.

#### 26. Collection Framework

#### 27. 어노테이션이란?

