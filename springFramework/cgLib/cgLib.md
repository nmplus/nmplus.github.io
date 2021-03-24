# CGLib 

- CGLib 소개 
- CGLIB는 코드 생성 라이브러리로서(Code Generator Library) 런타임에 동적으로 자바 클래스의 프록시를 생성해주는 기능을 제공한다. CGLIB를 사용하면 매우 쉽게 프록시 객체를 생성할 수 있으며, 성능 또한 우수하다. 더불어, 인터페이스가 아닌 클래스에 대해서 동적 프록시를 생성할 수 있기 때문에 다양한 프로젝트에서 널리 사용되고 있다. 예를 들어, Hibernate는 자바빈 객체에 대한 프록시를 생성할 때 CGLIB를 사용하며, Spring은 프록시 기반의 AOP를 구현할 때 CGLIB를 사용하고 있다. 

## CGLIB의 주요 구성 요소 
CGLIB는 프록시 생성과 관련된 모듈은 아래 그림과 같이 Enhancer 클래스, Callback 인터페이스 그리고 CallbackFilter 인터페이스이다. 이 세가지만 있으면 아주 손쉽게 원하는 프록시 객체를 생성할 수 있게 된다. 

![cgLib1](https://user-images.githubusercontent.com/58843821/112116709-e59a1800-8bfd-11eb-8989-e474b3d8a362.png)


Callback 인터페이스를 구현한 인터페이스를 두가지(MethodInterceptor, NoOp)만 표시했는데 이외에도 몇가지 인터페이스가 더 존재한다. 하지만, MethodInterceptor 인터페이스가 주로 사용되며, 본 글에서도 MethodInterceptor를 사용한 프록시 기능에 대해서만 살펴볼 것이다.  

원본 위치 <http://javacan.tistory.com/entry/114>  