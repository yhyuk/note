# [Java] 두 개의 List를 stream을 사용해서 비교하기

List를 비교하는 방법은 여러가지가 있다. 오늘은 java8부터 제공하는 stream을 사용해서 비교하는 방법을 알아보려고 한다.

### 예제1. List<String> 2개를 각각 비교해 중복 되지 않은 값 찾기

```java
void listTest() {
	List<String> oldList = Arrays.asList{"1", "2", "3", "4"};
	List<String> newList = Arrays.asList{"3", "4", "5", "6"};

	List<String> resultList1 = oldList.stream()
							.filter(old -> newList.stream().noneMatch(Predicate.isEuqal(old)))
							.collect(Collectors.toList());

	System.out.println(resultList1); // [1, 2]

	
	List<String> resultList2 = newList.stream()
							.filter(new -> oldList.stream().noneMatch(Predicate.isEqual(new)))
							.collect(Collectors.toList());

	System.out.println(resultList2); // [5, 6]
}
```

- noneMatch: 중복 X
- anyMatch: 중복 O

### 예제2. List<User> 2개를 id만 비교하여 중복되지 않은 값 찾기

```java
public static class User {
	private String id;
	private String name;
}
```

```java
void listTest() {
	List<User> targetList = Arrays.asList(User.builder().id("10001").name("홍길동").build(), User.builder().id("10002").name("아무개").build(), User.builder().id("10003").name("하하하").build());
	List<User> filterList = Arrays.asList(User.builder().id("10003").name("홍길동").build(), User.builder().id("10002").name("호호호").build());

	List<User> resultList = filterList.stream()
															.filter(filter -> targetList.stream()
																								.noneMatch(target -> filter.getId().equals(target.getId())))
																								.collect(Collectors.toList());

	System.out.println(resultList); // User[id=10003, name=홍길동]
}
```

- 위 예제1에서 사용한 Predicate.isEqual이 아닌 User 객체의 필요한 값(id)를 불러서 사용해서 비교한다.