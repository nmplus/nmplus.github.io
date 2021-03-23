# 생활코딩 정리

Github wiki로 이동. 

<JAVA>
코드 작성 -> 컴퓨터가 이해하는 언어로 컴파일 -> 컴파일된 프로그램 실행 
JDK : 소프트웨어 개발에 필요한 여러 도구들 제공 
JRE : 자바로 만들어진 프로그램을 구동하는데 필요한 실행환경 제공 

소스코드(Helloworld.java) -> ( 컴파일 javac ) -> class 파일 생성 -> ( 실행 java ) -> 결과 

  

* 문자 

 - 작은 따옴표 : 문자, 큰 따옴표 : 문자열 

예) 'A' : 문자   'B' : 문자  "AB" : 문자열 

   system.out.println ( "egoing \n\ "welcome programmin \"" );  

       출력 :   egoing 

                 welcome programming            

 

* 변수 

 - 변할 수 있는 데이터 (<-> 상수) 

 - int a : int는 데이터 형식, a는 변수의 이름 

  

* 주석 

 - // : 한 문장 주석 

 - /* ~ */ : 여러 문장 주석 

 - /** 

    *       : 자바독 주석 ( 주석 내용을 해석해 문서를 만들어줌 ) 

    */ 

  

* 데이터 타입 
- (정수) byte : 1byte, -128 ~ 127 

   Short : 2byte, -32,768 ~ 32,767 

   Int : 4byte, -2,147,483,648 ~ 2,147,483,647, 제일 많이 사용 

   Long : 8byte, -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 

 - (실수) float : 4byte, +- 1.40129846432481707e-45 ~ 3.40282346638528860e+38 

   double : 8byte, +- 4.94065645841246544e-324d ~ 1.79769313486231570e+308d    

      - double 주로 사용, float 사용 시 float a = 2.2F; 로 표시 

PS. 1byte는 bit로는 0,1로 이루어진 8자리의 bit로 구성된다. 
    음수,양수를 표현 해 하는 타입의 경우, 가장 앞의 비트를 이용하여 음수인지, 양수인지를 표현한다. 
   그렇기 때문에 정수 타입 중 byte는 1byte가 표현할 수 있는 값이 -128 ~127이 되는 것이다. 
   --> 음수,양수 Flag를 제외하면, 7자리.   0과 1만 표현 할 수 있으므로, 2^7(2의 7승) 값. 양수는 0이 있으므로, 값이 하나 적다. 
    

  

* 자동 형 변환 ( Implicit conversion, 암시적 형 변환 ) 

 - double a = 3.0F;   :  Float -> double 형으로 자동 형 변환 : 값이 3.0이 됨 

 - float a = 3.0;    :  형 변환 X ( Float이 double보다 작기 때문 ) 

 - 형 변환 가능 : byte -> short, char -> int -> long -> float -> double 

 - int a = 3; 

   Float b = 1.0F;                           

   Double c = a+b;                             

 -> int a가 float로 형 변환 되어 a가 3.0F가 됨 

     a+b = 4.0F, c의 데이터 타입은 double형이기 때문에 4.0F가 형 변환 되어 4.0이 됨 

  

* 명시적 형 변환 ( Explicit conversion ) 

 - ( 형 변환하려는 데이터타입 ) 데이터값 

 - float a = (float) 100.0; 

 - int b = (int) 100.0F; 

  

* 연산자 

 - + (더하기),  - (빼기),  * (곱하기),  / (나누기),  % (나머지)   

 - i++, ++i, i--, --i 

   int i =3; 

   System.out.println(++i);    -> 4 

   System.out.println(i++);    -> 4 

   System.out.println(i);       -> 5 

i++는 괄호 안에서 더해지는 것이 아니라 출력이 끝난 후에 값이 증가 

 - 우선순위 

1 

[ ] 

( ) 

. 

2 

++ 

-- 

+(양수) -(음수) 

~ 

! 

(type) 

new 

3 

* / % 

4 

 

+(더하기) -(빼기) 

+(문자열 결합 연산자) 

5 

<< 

>> 

>>> 

6 

<<= 

>>= 

instanceof 

7 

== 

!= 

8 

& 

9 

^ 

10 

| 

11 

&& 

12 

|| 

13 

? : 

14 

*= /= += -= %= 

<<= >>= >>>= 

&= ^= |= 

 

 

  

* 비교 

 - == (같다),   != (같지않다),   > < (크다 작다),   =>  <= (크거나 같다, 작거나 같다) 

 - 문자열은 == 대신 a.equals(b) 사용 

  

* if 문 

  if ( 조건문 ) { 

       if문이 true일 때 실행 되는 문장 

  } else if ( 조건문 ) {    

if문이 false이고 else if 문이 true 일 때 실행되는 문장 

  } else { 

if, else if 가 모두 false 일 때 실행되는 문장 

  } 

  

* switch 문 

 switch(1) {                           switch(1)일 때 case 1,2,3 실행, switch(2)일 땐 case 2,3 실행, switch(3)일 땐 case 3 실행 

  case 1 : ~                          switch( ) 괄호 안에 있는 숫자와 동일한 case 문 실행 후 그 다음 case문 실행 

  case 2 : ~                           

  case 3 : ~ }                       switch(2) { 

 switch(2) {                               case 1 : ~ 

  case 1 : ~                              case 2 : ~ 

  case 2 : ~                              break; 

  case 3 : ~ }                          case 3 : ~ 

                                          -> break문은 switch문 종료. Switch(2)일 때 case 2,3 이 실행되어야 하지만 case 2 까지만 실행 

  

* 논리 연산자 

 - && : and ( 좌항과 우항이 모두 참일 때 참 ) 

 - || : or ( 좌항과 우항 중 하나라도 참이면 참 ) 

 - ! : not ( 부정. true면 false가 되고, flase면 true가 됨 ) 

  

* while 문 

 while ( 조건 ) { 

      반복 실행 영역 

 } 

 

 int i = 0;                                                        

 while ( i<10 ) {                                      출력 -  값 : 0   

   system.out.println( " 값 : i " );                          ….0~9…. 

   i ++;                                                          값 : 9 

   } 

  

* for 문 

 - for ( 초기화; 종료조건; 반복실행 ) 

 

 for ( int i = 0; i < 10; i ++ ) { 

  if ( i == 5 ) 

     break;   -> 출력 : 0~4,       continue;  -> 출력 : 5를 뺀 0~9  

  system.out.println( " i " ); 

 } 

 - for-each : 뒤에는 어떠한 데이터의 집합. 앞에는 그 집합에 속한 것을 하나하나 변수에 할당 

   String[ ] members = { "최진혁", "최유빈", "한아람" }; 

     for (String e : members) { 

        System.out.println(e + "이 상담을 받았습니다"); 

     } 

    } 

  

* 배열 

 - 연관된 여러 개의 데이터를 하나의 변수에 담아 이를 쉽게 관리할 수 있게 해주는 기능 

 - String[] class = { "최진혁", "최유빈", "한아람" }; 

     system.out.println(class[0]);           

     출력 : 최진혁 

     [0] : 최진혁, [1] : 최유빈, [2] : 한아람 

 

 - 길이 확인 

  String[] class = new String[2]; 

  class[0] = " 최진혁 "; 

  system.out.println(class.length);   -> 3 

  class[1] = " 최유빈 ";                  

  system.out.println(class.length);   -> 3 : 담긴 값의 수를 알려주는게 아닌 수용가능한 값(length) 출력 

  

   String[] class = {"A", "B", "C"}; 

   for ( int i = 0; i < class.length; i++ ) { 

     String class2 = class[i]; 

     system.out.println( class2 + "출력" ); 

   } 

                   | | 위와 동일 

   String[] class = {"A", "B", "C"}; 

   for ( String e : class ) { 

     system.out.println ( e + " 출력" ); 

  } 

    A 출력 

    B 출력 

    C 출력 

  

* 메소드 

 public static void numbering() {                               -> 1. numbering 메소드 정의 

    .... 

 } 

 public static void main ( String[] args ) {                     -> 2. numbering 메소드 호출 

   numbering();     

 } 

 - 코드의 양을 줄여 유지보수가 유리해짐 

  

 public static void numbering ( int limit ) { 

 int i = 0; 

 while ( i<limit ) { 

   system.out.println(i); 

   i++; 

 } 

 public static void main ( String[] args ) { 

    numbering(5);          

 } 

 - 0~4 출력. Numbering( )이라는 메소드에 입력값을 주고 그 입력값에 따라 출력값이 달라짐 : Numbering(2)는 0,1 출력 

 - public static void numbering ( int limit ) 에서 int limit는 변수(매개변수, 파라미터). 입력값을 수용하기 위한 변수가 정의된 곳 

  

public static void numbering ( int init, int limit ) 

  numbering (3, 5);          -> 파라미터 int init, int limit에 순서대로 3,5 값이 들어감 

  

 - return : 메소드 종료. 뒤에 오는 값을 외부에 반환. Return 값이 여러 개면 첫번째 return만 실행 

   public static void ~  : void는 return 값이 없음 

  

* 객체 ( Object ) 

 - 객체1 : 댓글로직 - 변수, 메소드        -> 그룹화된 하나하나의 단위 

   객체2 : 본문로직 - 변수, 메소드 

 - Calculator c1 = new Calculator( );    -> 인스턴스화한다 ( 인스턴스 : 구체적인 객체 ) 

    데이터형              Calculator라는 객체를 생성해 c1에 대입 

  

* 클래스 

 - 클래스 : 설계도. 1개 

 - 인스턴스 : 설계도에 따라 만들어진 구체적인 제품. 여러개 

 - 멤버 : 구성원 

 public void setOperands ( int left, int right ) { 

  this.left = left; 

  this.right = right; 

 } 

 public static void main (String[] args) { 

  Calculator c1 = new Calculator ( ) ; 

  c1.setOperands (10, 20);                      -> c1 : 인스턴스 

  Calculator c2 = new Calculator ( ); 

  c2.setOperands (20, 40);                      -> 인스턴스(c1,c2)마다 서로 값이 다른 변수를 소유 

 } 

 class Calculator { 

  static double PI=3.14;                          -> 클래스 변수 static : 모든 인스턴스에서 공유 

  int left, right; 

  public void setOperands ( int left, int right ) {             -> 인스턴스 변수 : left, right 

      ... 

 } 

  

 - 인스턴스 메소드는 클래스 멤버에 접근할 수 있다 

 - 클래스 메소드는 인스턴스 멤버에 접근할 수 없다 

   ( 클래스가 먼저 만들어지기 때문에 인스턴스에 어떤 변수가 담겨져 있는지 확인하지 못함 ) 

                            클래스 

                             |    | 

                     인스턴스 인스턴스 

  

* 스코프(Scope) : 유효범위 

 - 해당 메소드 안에서 변수를 선언하면 해당 변수는 해당 메소드 안에서만 사용 가능 

 public class Scope { 

  static int i;              -> 전역변수 

  static void a() { 

     i = 0;                  -> 지역변수 ( static void a() { } 안에서만 유효 ) 

 } 

 public static void main ( String[] args ) { 

  for ( i=0; i<5; i++ ) { 

    a(); 

    system.out.println(i); 

 } 

  -> i=0 무한반복. 반복 안되게 하려면 int i=0; 또는 for문에 int추가 ( 해당 중괄호 내에서만 유효. 01234 출력 ) 

  

 Class C { 

   int v = 10;         -> 전역변수 

   void m ( ) { 

     int v = 20;       -> 지역변수 

     system.out.println(v);      -> 지역변수 적용 ( 같은 유효범위 내 )               출력 :  20  

     system.out.println(this.v);   -> this : 전역 유효범위                                          10 

  } 

} 

 public class Scope { 

  public static void main ( String[] args ) { 

    C c1 = new C ( ); 

    c1.m ( ); 

  } 

} 

  

* 생성자  

 - 객체 생성, 그 과정에서 최초로 수행해야 할 일이 있으면 그것을 할 수 있는 메소드를 정의할 기회 부여 

 Calculator c1 = new Calculator ( ); 

 c1.setOperands (10, 20); 

 c1.sum(); 

 c1.avg(); 

                 | | 위와 같음 

 Calculator c1 = new Calculaotr (10, 20);    -> 생성자 (인스턴스, 인스턴스) 

  c1.sum(); 

  c1.avg(); 

  

* 상속 

 - 부모 클래스의 객체가 갖고 있었던 변수나 메소드를 그대로 자식클래스에서 쓰거나 추가하여 사용 

 Sub c1 = new Sub ( ); 

  c1.setOperands (10, 20); 

  c1.subtract ( ); 

  

 class Sub extends Calculator {           -> extends : Sub 클래스가 Calculator 클래스를 확장(상속) 했다 

    public void subtract() { 

       system.out.println ~ 

 } 

  

 - super( ~ ) : 부모 클래스의 생성자 

 - 오버라이딩 : 상속을 받아 부모클래스의 메소드를 그대로 쓰지 않고  

                    자식클래스가 재정의하고 기능을 변경하는 방법 

                     1. 부모클래스의 반환타입과 자식클래스의 반환타입은 일치해야함 ( void=void, int=int ) 

                     2. 메소드의 이름이 같아야 함 

                     3. 메소드 매개변수의 개수와 데이터 타입, 순서가 같아야함 

 - 오버로딩 : 클래스에 메소드를 정의할 때 이름이 같지만 서로 다른 매개변수 형식을 지닌 메소드를 

                 여러개 정의할 수 있는 방법 

                  public void setOperands ( int left, int right ) { ~ 

                  public void setOperands ( int left, int right, int third) { ~ 

  

* 패키지 

 - 패키지 A - A class 

   패키지 B - B class 

   B패키지에서 A a = new A (); 사용시 A가 다른 패키지이기 때문에 오류 -> import A.*; 맨 위에 추가 후 가능 

  

* API ( Application Programming Interface ) 

 - 기반이 되는 시스템(웹 브라우저 등)이 우리에게 제공한 인터페이스를 응용해서 어떤 소프트웨어를 만들도록 제공 

 - System.out.println( ); 에서 

   System : 클래스 

   out : system 클래스의 멤버변수. println( ) 메소드를 가지고 있는 객체 

   println( ) : 메소드. system 클래스에 속한 out 변수의 소속 

   System.out : 인스턴스화 X -> static 필드 

   import java.lang.*;  -> system.out 사용시 자동 import (System 클래스가 java.lang 소속) 

 - API 참고 사이트 : http://docs.oracle.com/javase/ 

                          Reference -> Java SE API Documentation 

  

* 접근 제어자 

 - public : 어디에서나 그 클래스의 메소드를 호출해서 사용가능 

 - private : 외부 클래스에서는 사용 불가 ( 사용자가 마음대로 못바꾸게 하기위함 ) 

  

public 

protected 

default 

private 

같은 패키지, 같은 클래스 

O 

O 

O 

O 

같은 패키지, 상속 관계 

O 

O 

O 

X 

같은 패키지, 상속 관계 X 

O 

O 

O 

X 

다른 패키지, 상속 관계 

O 

O 

X 

X 

다른 패키지, 상속 관계 X 

O 

X 

X 

X 

 - 클래스의 접근제어자는 public, default만 가능 

   public class A {     혹은     (default) class B { 

  

* abstract ( 추상 ) 

 - 반드시 그 클래스를 상속하는 클래스를 만들고, 그렇게 상속한 클래스를 사용해야함 

  abstract class A { 

    public abstract int b ( ) ;   -> int b( ){ ~ } 중괄호 사용 안함. 대신 자식 클래스에서 로직 구현 

  Class B extends A { 

    public int b ( ) {               -> 자식클래스. 꼭 ! ! 구현 

    return 1; 

   } 

 } 

 public class Abstract { 

   public static void main ( String[] args ) { 

     B obj = new B ( ); 

  } 

 } 

 - 추상 클래스에는 공통적인 로직을 구현하고 추상클래스를 상속한 자식클래스에서 용도에 따라 

   달라지는 구현을 사용자가 직접 하도록 유도하거나 규제하기 위해 사용 

  

* final 

 - 한 번 설정된 값을 바꾸지 못함 

 Class A {                           상속(extends) 불가               Class B extends A { 

  final void b ( ) {                             ->                          void b ( ) { 

  }                                       오버라이딩도 불가                 } 

 }                                                                              }  

  

* 인터페이스 

 - 어떤 클래스에서 특정한 인터페이스를 사용한다면 그 클래스가 반드시 해당 인터페이스에 포함된 메소드를 구현하도록 함 

 interface I1 { 

   public void x ( ) ; {                         -> 인터페이스는 반드시 public 사용 

 interface I2 {                                  -> 여러 개 인터페이스 가능 ( I1, I2, … ) 

   public void z ( ) ; { 

 class A implements I1, I2 { 

   public void x ( ) {                          -> 메소드 반드시 구현 

   }  

   public void z ( ) { 

   } 

 } 

  

* 다형성 

 - 한 메소드나 클래스가 다양한 방식으로 동작한다는 것을 의미 

   a( )라는 메소드가 있을 때 이 메소드가 상황에 따라 다르게 동작하는 것 

 A obj = new B ( )             -> class B extends A 인 상태 

 A 클래스 행세를 하고 있지만 B 클래스 의미 

  

* 예외 

 - 일반적이지 않은 상황에서 우리가 기획했던 바와 다르게 발생하는 문제 

 try { 

  예외의 발생이 예상되는 로직 

 } catch (Exception e) {                          -> Exception : 모든 예외를 포괄하는 예외 

  예외가 발생했을 때 실행되는 로직 

 } finally { 

  예외 여부와 관계없이 실행되는 로직 

 } 

 - catch로직에 system.out.println(e.getMessage( )); : 무슨 예외 상황인지 출력해 줌 

                                            e.toString( ) : 좀 더 자세히 출력 

                                            e.PrintStackTrace( ) : 아주 자세히 출력 

  

 Class B { 

   void run ( ) throws FileNotFoundException {         -> throws : 예외책임을 C클래스의 run( ) 메소드로 넘김 

     Class C { 

        void run ( ) { 

         try { 

         } catch { 

         } .... 

 - 사용해야 할 상황 

  IllegalArgumentException : 매개변수가 의도하지 않은 상황을 유발할 때 

   IllegalStateException : 메소드를 호출할 수 있는 상태가 아닐 때 

   NullPointerException : 매개변수 값이 Null 일 때 

   IndexOutOfBoundsException : 인덱스 매개변수 값이 범위를 벗어날 때 

   ArithmeticException : 산술적인 연산에 오류가 있을 때 

 - 예외 클래스의 상속 관계 

                           throwable 

                           |           | 

                      Error          Exception 

                                      |           | 

                         IOException        RuntimeException  

         검사예외 ( try/catch 필수 )                 |      비검사예외 

                                                 ArithmeticException        

  

* toString( ) 

 - 객체의 내용을 문자화 

 System.out.println (c1); 

            | | 

 System.out.println (c1.toString( ));      -> toString()을 주로 생략 

 - 모든 클래스는 extends Object가 생략되어 있음 

   Object 클래스 안에는 toString( ) 메소드가 정의되어 있기 때문에 생략 가능 

  

* equals ( ) 

 - 어떤 두 개의 인스턴스가 서로 같은 인스턴스인지 비교 

 - 객체를 비교하는 것이 아니라 원시 데이터형(byte, short, int, long, float, double, boolean, char)과 같은 특수한 형태의 데이터 타입을 사용할 때는 비교 연산자를 쓰고 

    String이나 객체를 비교할 때는 equals ( ) 사용 

 public boolean equals ( Object obj ) { 

    return true & false; 

 } 

  

* Clone ( ) 

 - 어떤 객체가 있고 그 객체와 똑같은 것이 필요할 때 그 객체를 복제 

  1. Cloneable 이라는 빈 인터페이스를 만들어 복제 가능한 객체가 있다는 사실을 자바 가상 머신에게 알림 

  2. Clone ( ) 메소드의 접근자는 privated 이기 때문에 원래 클래스에  

       public Oject clone ( ) { 

       return super.clone ( ); }   추가 

  3. CloneNotSupportedException은 Exception을 상속하기 때문에 검사 예외 이므로  

    public Object clone ( ) throws CloneNotSupportedException { 

         return.super.clone( ); 추가. 

      오류난 부분에 try / catch 추가 

  4. 또 오류가 난다면 명시적 형변환 고려 

  

  

* enum 

 - 열거형(enumerated type). 서로 연관된 상수의 집합 

 Class Fruit { 

   public static final Fruit APPLE = new Fruit ( ); 

   public static final Fruit PEACH = new Fruit ( ); 

   public static final Fruit BANANA = new Fruit ( ); 

 } 

                |  | 위와 동일 

 enum Fruit { 

    APPLE, PEACH, BANANA; 

  Fruit ( ) { 

    system.out.println ( "과일" + this ); }         

   } 

 출력 : 과일 APPLE 

          과일 PEACH 

          과일 BANANA 

  

 Public static void main ( String[] args ) { 

   for ( Fruit f : Fruit.values( )) { 

     system.out.println ( f + ", " + f.getColor( )); 

  } 

 } 

 출력 : APPLE 

         PEACH 

         BANANA 

  

* 참조 ( Refernece ) 

 - 원래 값을 바꾸면 참조한 값도 같이 바뀜 ( <-> 복제 : 원래 값을 바꿔도 복사한 값은 바뀌지 않음 ) 

 A a = new A ( );             ->  a,b가 new A( ); 참조 

 A b = a; 

 - 기본 데이터 타입이 지정돼 있다면 각 변수가 기본 데이터 타입의 데이터를 직접 갖고 있다는 것. 

   기본 데이터 타입이 아닌 변수를 만들었다는 것은 인스턴스를 참조하고 있다는 것. 

   new를 이용해 인스턴스를 만드는 모든 데이터 타입은 참조형 & 참조 자료형 & 참조 데이터형 

 public static void runRefernece ( ) { 

  A a = new A (1); 

  A b = a; 

  b.id = 2; 

   system.out.println ( "runRefernce," + a.id );           출력 : 2 ( A인스턴스의 id값을 가져옴 ) 

 } 

 -> b.id 위에 b=new A(2); 를 넣으면 a.id는 1을 출력 

     b변수가 new A(1);로 생성한 인스턴스를 가리키는 것이 아니라 new A(2)로 생성한 인스턴스를 가리키기 

     때문에 a와 b가 각자 다른 인스턴스를 가리킴* 

  

* 제네릭 

 Class Person <T> { 

   public T info;              -> info의 데이터타입 = T  

 } 

 Person <String> P1 = new Person <String> ( ); 

 Person <StringBuilder> P2 = new Person <StringBilder> ( ); 

 -> T에 올 수 있는 데이터 타입은 참조형만 가능. 기본형(int, char, double 등) 은 불가능 

     기본형 사용하려면 래퍼(wrapper) 클래스 사용. ( int->Integer. Integer i = new Integer(1); ) 

 - Person <Employee, Integer> P1 = new Person <Employee, Integer> (e, i); 

                                                  |  | 생략 

                                Person P1 = new Person (e,i); 

 - 메소드에도 사용 가능 

  

* 컬렉션 프레임워크 

 String[] arrayObj = new String[2]; 

   arrayObj [0] = "one"; 

   arrayObj [1] = "two"; 

   for (int i=0; i<arrayObj.length; i++) { 

     System.out.println(arrayObj[i]); { 

                   | | 위와 같음 

 ArrayList<String>a1 = new ArrayList<String> ( );     -> <String> : 제네릭 (강제 형변환) 

   a1.add("one"); 

   a1.add("two"); 

   for (int i=0; i<a1.size(); i++) { 

    String val=a1.get (i); 

    System.out.println(val); 

   } 

  

 Collection ㅡ Set ㅡ Hashset 

                        ㅡ LinkedHashSet 

                        ㅡ TreeSet 

               ㅡ List ㅡ ArrayList 

                        ㅡ Vector 

                        ㅡ LinkedList 

               ㅡ Queue ㅡ PriorityQueue 

  

 Map ㅡ SortedMap ㅡ TreeMap 

        ㅡ HashTable 

        ㅡ LinkedHashMap 

        ㅡ HashMap 

  

 - set : 중복 X 

   A.add(1); A.add(1); A.add(2);    -> 1,2 출력 

   List : 중복 O 

   A.add(1); A.add(1); A.add(2);     -> 1,1,2 출력 

  

- HashSet 

  A = 1,2,3      B = 3,4,5     C = 1,2 

  System.out.println(A.containsAll(B))     -> containsAll : 부분집합. flase 

  System.out.println(A.containsAll(C))     -> true 

  -> addAll : 합집합, retainAll : 교집합, removeAll : 차집합 

  

* Iterator 

 - 컨테이너에 담긴 값을 하나씩 꺼내서 처리할 수 있게 해줌 

  Iterator hi = A.iterator( ); 

   while ( hi.hasNext( ) ) { 

      system.out.println(hi.next( )); 

   } 

  -> hasNext ( ) : 다음값이 존재하면 true . 1호출 

      hi.next( ) 에서 1 지운 후 hasNext( )로 2가 있는지 확인. 

      2가 출력된 후 next( ) 에서 2값이 hi에서 지워짐 

      hasNext( )에 다음 값이 없으면 false. while문 끝 

  

* Map (HashMap) 

      key : "one"   "two"   "three"   "01"        -> 중복 X 

    value :    1        2         3          2          -> 중복 O 

 HashMap<String, Integer> a = new HashMap<String, Integer> ( ); 

 a.put("one", 1); 

 system.out.println(a.get("one"));             출력 : 1 
