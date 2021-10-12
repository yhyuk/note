# [MyBatis] if - else 사용하기 (choose)

먼저 Mybatis 에서는 단일if문은 제공하지만, if~else if 문을 사용할 수가 없다.

하지만 <choose> </choose> 문을 if ~ else if 문 처럼 사용이 가능하다.

### 예제1. 조건이 단일(1개) 일 때

```html
<choose>
	<when test = "조건">
		위에 조건이 맞을시 실행할 구문
	</when>
	<otherwise>
		조건1이 틀릴경우 실행할 구문
	</otherwise>
</choose>
```

### 예제2. 조건이 여러개(N개) 일 때

```html
<choose>
	<when test = "조건1"> 
		위에 조건이 맞을시 실행할 구문
	</when>
	<when test = "조건2"> 
		위에 조건이 맞을시 실행할 구문
	</when>
	<when test = "조건3"> 
		위에 조건이 맞을시 실행할 구문
	</when>
	<otherwise>
		조건1, 조건2, 조건3이 틀릴경우 실행할 구문
	</otherwise>
</choose>
```

### 예제3. 조건에서 연산자(and, or) 사용

```html
<choose>
	<when test = "조건1 and 조건2">
		위에 조건이 맞을시 실행할 구문
	</when>
	<when test = "조건3 or 조건4">
		위에 조건이 맞을시 실행할 구문
	</when>
	<otherwise>
		위 조건이 전부 틀릴경우 실행할 구문
	</otherwise>
</choose>
```