# [Java] 깊은복사와 얕은복사(Call By Value & Call By Reference)

자바를 떠나서 프로그래밍을 하다 보면 꼭 알아야할 개념 중 하나인 Call By Value, Call By Reference에 대해 알아보자.

### Call By Value

- 값을 호출 하는것을 의미하며 전달 받은 값을 복사하여 처리한다.
- 전달 받은 값을 변경하여도 원본은 변경되지 않는다.

### Call By Reference

- 참조에 의한 호출을 의미하며, 전달 받은 값을 직접 참조한다.
- 전달 받은 값을 변경할 경우 원본도 같이 변경이 된다.

그렇다면 자바에서의 Call By Value와 Call By Reference는 어떻게 적용이 될까? 

- 기본 자료형 변수가 파라미터 → **값 (깊은 복사)**
- Array, List 등의 변수가 파라미터 → **주소(얕은 복사)**

아직 정확하게 깊은 복사와 얕은 복사가 어떤 건지 이해가 안되니, 예제로 정의와 장단점을 살펴보도록 하자.

### 깊은 복사(Deep Copy)

- 정의: **새로운 메모리 공간에 값(Value)을 복사**하는 것이다.
- 장점: 여러 객체가 동시에 수정되는 일이 발생하지 않아, 변경에는 안전하다.
- 단점: 객체 생성 비용이 비싸며, 메모리를 많이 점유한다.
- 특정 객체를 깊은 복사하는 경우 Clonable 인터페이스를 활용하, clone()메소드를 Overring 해주어야 깊은 복사가 가능하다.

```java
public class DeepCopy {
	public static void main(String[] args) {
		int[] list = {1, 2, 3};
		int[] deep_coopy = list.clone();

		System.out.println(list);
		System.out.println(deep_copy);
	}
}
```

![Untitled](%5BJava%5D%20%E1%84%80%E1%85%B5%E1%87%81%E1%84%8B%E1%85%B3%E1%86%AB%E1%84%87%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AA%20%E1%84%8B%E1%85%A3%E1%87%80%E1%84%8B%E1%85%B3%E1%86%AB%E1%84%87%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A1(Call%20By%20Value%20&%20C%20e22fb1f2710b41688b2343bca4fdcd6d/Untitled.png)

### 얕은 복사(Shallow Copy)

- 정의: **주소값이 복사**되는 것을 말한다.
- 장점: 같은 객체를 공유하므로 메모리를 절약하고, 빠른 장점이 존재한다. 참조에 의한 호출(Call By Reference)에서 얕은 복사가 이루어 지는 이유 중 하나이기도 하다.
- 단점: 두 개 이상의 객체가 같은 대상을 가르키고 있기 때문에, 의도치 않게 여러 개의 객체가 동시에 수정될 수 있다.

```java
public class ShallowCopy {
	public static void main(String[] args) {
		int[] list = {1, 2, 3};
		int[] shallow_copy = list;

		System.out.println(list);
		System.out.println(shallow_copy);
	}
}
```

![Untitled](%5BJava%5D%20%E1%84%80%E1%85%B5%E1%87%81%E1%84%8B%E1%85%B3%E1%86%AB%E1%84%87%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AA%20%E1%84%8B%E1%85%A3%E1%87%80%E1%84%8B%E1%85%B3%E1%86%AB%E1%84%87%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A1(Call%20By%20Value%20&%20C%20e22fb1f2710b41688b2343bca4fdcd6d/Untitled%201.png)

### Clonable 인터페이스

```java
class Copy implements Clonable {
	private String name;

	// 새로운 Object를 넘겨주는 clone메서드를 오버라이딩 한다.
	public Object clone() thorws ClonenotSupportedException {
		return super.clone();
	}
}

public class DeepCopy {
	public static void main(String[] args) throws CloneNotSupportedException {
		Copy a = new Copy();
		Copy b = (Copy)a.clone(); // Object 클래스(부모 클래스)를 넘겨주므로, 캐스팅 필요

		System.out.println(a);
		System.out.println(b);
	}
}
```

> reference
> 
- [https://yeonyeon.tistory.com/122](https://yeonyeon.tistory.com/122)
- [https://sskl660.tistory.com/43](https://sskl660.tistory.com/43)