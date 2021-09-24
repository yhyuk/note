# [MySQL] - JOIN (INNER, OUTER)

DB 쿼리 작성을 할 때 가장 중요하고 많이 쓰이는 것 중 하나인 Join에 대해서 알아보자.

### **JOIN 정의**

데이터베이스 내의 여러 테이블에서 가져온 레코드를 조합하여 하나의 테이블이나 결과 집합으로 표현해 준다.

이러한 JOIN은 보통 SELECT 문과 함께 자주 사용된다.

### **JOIN 종류**

INNER JOIN : A, B 두 테이블이 존재할 때 두 테이블의 교집합, **두 테이블에서 모두 일치하는 값을 리턴**(반환)한다.

OUTER JOIN

- LEFT OUTER JOIN : A, B 두 테이블이 존재할 때 **A테이블(왼쪽) 전체 값**과 **B테이블(오른쪽)**과 **일치하는 값을 리턴**(반환)한다.
- RIGHT OUTER JOIN : A, B 두 테이블이 존재할 때 **A테이블(왼쪽)**과 **B테이블(오른쪽) 전체 값**과 **일치하는 값을 리턴**(반환)한다.

![https://blog.kakaocdn.net/dn/b5n975/btrfXGrzvlk/FWwkkMwzSKPPam6LwHw57k/img.png](https://blog.kakaocdn.net/dn/b5n975/btrfXGrzvlk/FWwkkMwzSKPPam6LwHw57k/img.png)

- 참고로 MySQL에서는 JOIN == INNER JOIN == CROSS JOIN이 모두 같은 의미로 사용된다.
- LEFT JOIN == LEFT OUTER JOIN , RIGHT JOIN == RIGHT OUTER JOIN

### **INNER JOIN 문법 및 예제**

> 문법

```
SELECT *
FROM A테이블
INNER JOIN B테이블
ON 조건
```

> 예제

![https://blog.kakaocdn.net/dn/ux3kD/btrfXx2uHAa/meGGnflJiTUWJAzBoe6sSk/img.png](https://blog.kakaocdn.net/dn/ux3kD/btrfXx2uHAa/meGGnflJiTUWJAzBoe6sSk/img.png)

JOIN 예제에 사용될 두 개의 테이블 내용이다.

```
방법1.
SELECT *
FROM Reservation R
INNER JOIN Customer C
ON R.name = C.name

방법2.
SELECT *
FROM Reservation R, Customer C
WHERE R.name = C.name
```

- 방법1과 2는 똑같은 결과값을 가져오며 MySQL에서 사용할 수 있는 방식 중 하나이다.
- 실행 결과는 Reservation의 Name과 Customer의 Name이 일치하는 값을 가져오는 결과 값이다. 결과에서도 알 수 있듯이 Customer테이블의 전우치라는 Name은 Reservation테이블에 없기 때문에 제외 되었다.

> 실행결과

![https://blog.kakaocdn.net/dn/s3cG4/btrfTJ4qgiN/nHbZqAXXHID2FV1fFlxUY0/img.png](https://blog.kakaocdn.net/dn/s3cG4/btrfTJ4qgiN/nHbZqAXXHID2FV1fFlxUY0/img.png)

### 

### **LEFT OUTER JOIN**

> 문법

```
SELECT *
FROM A테이블
LEFT OUTER JOIN B테이블
ON 조건
```

> 예제

```
SELECT *
FROM Reservation R
LEFT OUTER JOIN Customer C
ON R.Name = C.Name
WHERE R.ReserveDate > '2016-02-01';
```

- Reservation 테이블의 Name 필드를 기준으로 Customer 테이블의 Name 필드와 일치하는 레코드만을 LEFT JOIN으로 가져온 후, 그 중에서 ReserveDate 필드의 값이 2016년 02월 01일 이후인 레코드만을 선택하는 예제이다.
- 위의 예제에서 두 개의 Name 값이 일치하면, INNER JOIN과 같이 두 테이블의 모든 필드를 그대로 가져온다. 하지만 두 개의 Name 값이 일치하지 않는 경우에는 Customer 테이블의 모든 필드를 NULL로 표시된다.

> 실행결과

![https://blog.kakaocdn.net/dn/xrIuq/btrfXIbSKOU/ZXwOxZvnMebDczNeZPjPg0/img.png](https://blog.kakaocdn.net/dn/xrIuq/btrfXIbSKOU/ZXwOxZvnMebDczNeZPjPg0/img.png)

### **RIGHT OUTER JOIN**

> 문법

```
SELECT *
FROM A테이블
RIGHT OUTER JOIN B테이블
ON 조건
```

> 예제

```
SELECT *
FROM Reservation
RIGHT JOIN Customer
ON Reservation.Name = Customer.Name;
```

- RIGHT JOIN은 LEFT 조인과는 반대로 두 번째 테이블을 기준으로, 첫 번째 테이블을 조합하는 JOIN이다.
- Customer 테이블의 Name 필드를 기준으로 Reservation 테이블의 Name 필드와 일치하는 레코드만을 RIGHT JOIN으로 가져오는 예제이다.
- 위의 예제에서 두 개의 Name 값이 일치하면, INNER JOIN과 같이 두 테이블의 모든 필드를 그대로 가져온다. 하지만 두 개의 Name 값이 일치하지 않는 경우에는 Reservation 테이블의 모든 필드를 NULL로 표시된다.

> 실행결과

![https://blog.kakaocdn.net/dn/bJkoiB/btrfV9nwxJD/ROYC30bb33jBk5fIZPY8l0/img.png](https://blog.kakaocdn.net/dn/bJkoiB/btrfV9nwxJD/ROYC30bb33jBk5fIZPY8l0/img.png)

### **INNER vs OUTER 속도 차이?**

대부분의 경우, **OUTER JOIN이 느리다**. ( INNER > OUTER )

OUTER JOIN은 INNER JOIN의 모든 일 + 결과 null-extending*을 수행해야하고, 더 여러 개의 레코드를 반환한다.

- null-extending: 두 테이블 A와 B를 LEFT JOIN할 때, B 테이블에 상응하는 값이 없으면 NULL 값을 반환한다.

결론적으로, OUTER JOIN은 INNER JOIN과 달리 **추가적인 작업을 수행**한다. **테이블들에서 일치하지 않는 행과 NULL 값도 가져와야한다.**