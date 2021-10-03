# [Java] 데이터 타입 Integer와 Int의 차이

## 데이터 타입 Integer와 Int의 차이

```java
int n1;
Integer n2;
```

Java에서 int를 선언할 때와, Integer를 선언할 때의 차이점이 뭘까? 그 부분에 대해서 알아보려 한다.

### ***Int***

- **primitive 자료형**(long, float, double) 이다.
- 산술 연산이 가능하다.
- **null로 초기화 할 수 없다.**

### ***Integer***

- **Wrapper 클래스**(한 객체를 의미) 이다.
- Unboxing을 하지 않으면 산술 연산이 불가능 하지만, **null 값을 처리할 수 있다.**
- null 값 처리가 용이하기 때문에 SQL과 연동할 경우에 처리를 원할하게 할 수 있다.
- DB에서 자료형이 정수형이지만 null 값이 필요한 경우 VO에서 Integer를 사용할 수 있다.

### ***Wrapper 클래스란?***

- Java는 데이터로서 클래스와 객체 외에 기초(Primitive) 타입을 가진다. 그렇기 때문에 **기본형 타입(Primitive 자료형)**과 **객체 참조(클래스)** 같은 **두 가지 타입의 관리 데이터를 가진다.**
- 경우에 따라서 기본형 타입을 객체로 사용하는 경우가 있으며, 이러한 경우 기본형 타입 값을 객체로 표현해야 한다.
- 이 때, Wrapper 클래스를 사용하는데 특정 기본형 타입으로 나타낸다. 예를 들어 **Integer 클래스는 간단한 정수값을 나타내며 객체는 하나의 int값을 저장할 수 있다.**

### ***int와 Integer간의 변환***

먼저, Integer에서 나왔던 Unboxing에 대해 알아보자.

- Boxing: Primitive 자료형 → Wrapper 클래스
- Unboxing: Wrapper 클래스 → Primitive 자료형

```java
// 1. Integer n2를 int n1으로 변환 -> Unboxing
int n1 = n2.intValue();

// 2. int n1를 Integer n2으로 변환 -> Boxing
Integer n2 = new Integer(n1);
```

### ***Auto boxing / unboxing***

자바에서는 모든 경우는 아니지만, 대부분의 경우에는 자동으로 boxing / unboxing을 해준다.

```java
int n1 = 1;
Integer integer = n1; // int     -> Integer (Auto boxing)
int n2 = integer;     // Integer -> int     (Auto unboxing)
```

å

### ***reference***

[https://docs.oracle.com/en/java/javase/16/docs/api/java.base/java/lang/Integer.html](https://docs.oracle.com/en/java/javase/16/docs/api/java.base/java/lang/Integer.html)

[https://hochoon-dev.tistory.com/entry/Java-데이터-타입-Integer와-int의-차이](https://hochoon-dev.tistory.com/entry/Java-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-Integer%EC%99%80-int%EC%9D%98-%EC%B0%A8%EC%9D%B4)

[https://www.w3schools.com/java/java_data_types.asp](https://www.w3schools.com/java/java_data_types.asp)