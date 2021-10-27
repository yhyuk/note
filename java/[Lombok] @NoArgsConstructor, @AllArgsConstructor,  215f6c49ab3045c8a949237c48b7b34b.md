# [Lombok] @NoArgsConstructor, @AllArgsConstructor, @RequireArgsConstructor

Lombok에서 제공하는 기능 중 가장 대표적인 @Date, @Getter, @Setter 외에도 **생성자를 자동 생성 해주는 @NoArgsConstructor, @AllArgsConstructor, @RequrieArgsConstructor**에 대해 어떤것을 의미하는지 알아보자.

### @NoArgsConstructor

- 파라미터가 없는 기본 생성자를 생성한다.

### @AllArgsConstructor

- 모든 필드 값을 파라미터로 받는 생성자를 생성한다.

### @RequireArgsConstructor

- final이나 @NonNull인 필드 값만 파라미터로 받는 생성자를 생성한다.

### 예제

```java
@NoArgsConstructor
@AllArgsConstructor
@RequireArgsConstructor
public class User {

	private Long id;

	@NonNull
	private String name;

	@NonNull
	private String pw;

	private int age;

}
```

```java
User user1 = new User(); // @NoArgsConstructor
User user2 = new User("user1", "1234"); // @AllArgsConStructor
User user3 = new User(10000L, "user3", "1234", null); // @RequireArgsConstructor
```