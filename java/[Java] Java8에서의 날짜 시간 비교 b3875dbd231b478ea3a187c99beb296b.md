# [Java] Java8에서의 날짜/시간 비교

Java8 이전에는 흔히 알고 있는 Date, Calendar를 통해 날짜시간을 비교했었는데 불편한 사항이 많았다. 

하지만 Java8 부터는 LocalDateTime, LocalDate, LocalTime, ZonedDateTime을 제공하기 때문에 기존의 불편한 사항이 많이 해소 되었다. 

그래서 오늘은 많이 쓰이는 LocalDateTime을 이용한 대표적으로 날짜/시간 비교하는 함수를 정리해두려고 한다.

### isBefore()

- 인자보다 과거일 때 true 반환

```java
LocalDateTime oldDate = LocalDateTime.parse("2021-11-10T10:11:15.000");
LocalDateTime newDate = LocalDateTime.parse("2021-12-16T10:11:15.000");

if (oldDate.isBefore(newDate)) {
	System.out.println("과거 날짜입니다.");
}
```

### isAfter()

- 인자보다 미래일 때 true 반환

```java
LocalDateTime oldDate = LocalDateTime.parse("2021-11-10T10:11:15.000");
LocalDateTime newDate = LocalDateTime.parse("2021-12-16T10:11:15.000");

if (newDate.isBefore(oldDate)) {
	System.out.println("미래 날짜입니다.");
}
```

### isEqual()

- 인자와 같은 시간일 때 true 반환

```java
LocalDateTime oldDate = LocalDateTime.parse("2021-11-10T10:11:15.000");
LocalDateTime newDate = LocalDateTime.parse("2021-11-10T10:11:15.000");

if (oldDate.isBefore(newDate)) {
	System.out.println("같은 날짜입니다.");
}
```

추가로 Java8 이전은 Date, Calendar를 통해 날짜를 비교할 수 있다. 하지만 앞서 말했듯이 불편 사항이 많다.

> reference
> 

[https://stackoverflow.com/questions/32447885/java-comparator-for-two-localdatetimes](https://stackoverflow.com/questions/32447885/java-comparator-for-two-localdatetimes)