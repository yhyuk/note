# [Spring Boot] - RESTFul 하게 URI 설계하기

### **REST API란?**

> 약어

**RE**presentational

**S**tate

**T**ransfer

> 정의

- 클라이언트 ↔ 서버의 통신방식
- URI와 HTTP를 이용한, 통신 목적의 아키텍쳐 스타일(유형)

* URI (Uniform Resource Identifier): 문서, 그림, 영상 등의 자원 식별용 이름(경로)

- 네트워크 아키텍쳐 원리 모음 -> "사이트의 구성 원리"
- REST API를 제공하는 시스템은 RESTFul이다.

REST는 아키텍처 스타일이다. 이는 아키텍처 제작 시 사용되는 가이드(지침) 정도의 의미로 사용되며 명확히 준수해야할 표준은 없다!

그렇다보니 겉으로는 REST를 표방하고 있으나 특히 일관된 인터페이스 조건을 준수하지 않아 REST가 아닌 경우가 많다.

### **REST API 6가지 제한조건**

**1. 클라이언트 / 서버 구조**

- 클라이언트는 서버에 요청(request) 메세지를 전송하고
- 서버는 요청에 대한 응답(response) 메세지를 전송한다.

**2. 무상태 (Stateless)**

- 세션 등 이전 상황(문맥) 없이도 통신할 수 있다.

**3. 캐리 처리 가능 (Cacheable)**

- 서버의 응답 메시지는 케싱(저장 후 재사용)될 수도 있다.

**4. 계층화 (Layered System)**

- 계층별로 기능이 분리된다. 그러므로 중간 계층의 기능(로드 밸런싱, 서버 증설, 인증 시스템 도입 등)이 변경 되어도 통신에 영향을 주지 않는다.

**5. 주문형 코드 (Code On demand) (Optional)**

- 손쉬운 데이터 처리를 위해 서버는 클라이언트에서 실행될 스크립트를 전송할 수 있다.

**6. 인터페이스 일관성(Uniform interface)**

- URI 사용, HTTP 메소드 사용, RPC 미호출 등의 지정된 인터페이스를 준수한다.

1 ~ 5번까지는 모두 HTTP 상에 녹아있다.(존재한다) 우리 개발자의 입장에서는 **인터페이스 일관성**만 신경쓰면 REST하게 사이트를 만들 수 있다.

* REST하게 만든다?  URL 주소만 보고도 수행하려는 동작을 눈치챌 수 있게 만드는 것

### **REST 방식의 URI 설계**

> URI 예시

![https://blog.kakaocdn.net/dn/bKIGiV/btrfXyt6er5/iGDS5LrpcX2qzOIk7L7jk1/img.png](https://blog.kakaocdn.net/dn/bKIGiV/btrfXyt6er5/iGDS5LrpcX2qzOIk7L7jk1/img.png)

- 메소드는 GET, POST, PUT, DELETE로 명칭을 보면 가져오기, 보내기, 수정하기, 삭제하기 등 쉽게 알 수 있다.
- 리소스는 데이터베이스 상에 들어가있는 내용을 담고 있다고 생각 하면된다.

> URI를 그럼 어떻게 만들까?

![https://blog.kakaocdn.net/dn/z46P0/btrfXxBXJLf/bLDTzL2LKbE6zWV5yTcHM1/img.png](https://blog.kakaocdn.net/dn/z46P0/btrfXxBXJLf/bLDTzL2LKbE6zWV5yTcHM1/img.png)

- 이런식으로 REST하게 URI를 구성하게 되면 장점으로 **간결하고 일관성 있게 URI를 구성할 수 있다**.

> 언제 어떤 메소드를 써야할까?

![https://blog.kakaocdn.net/dn/C2xJb/btrf1i5mu4R/RkBweocqbHCkIssjMu81Y0/img.png](https://blog.kakaocdn.net/dn/C2xJb/btrf1i5mu4R/RkBweocqbHCkIssjMu81Y0/img.png)

- 보통 GET, POST, PUT, DELETE의 쓰임새는 정해져있지만, 만약 헷갈린다면 위 표를 살펴보자

> 어떤방식이 RESTFul 방식 일까?

![https://blog.kakaocdn.net/dn/bd04QX/btrfVs9hqwV/3p3CFjQrjdVKpTmaolyux0/img.png](https://blog.kakaocdn.net/dn/bd04QX/btrfVs9hqwV/3p3CFjQrjdVKpTmaolyux0/img.png)

- X 표시가 되어있는것은 기존에 많이 이용하고 봤던 방식이며 절대 사용하면 안되는 것이 아닌 REST 방식이 아니라는 의미로 생각하면 된다.
- O 표시로 되어있는 것이 당연 REST 방식으로 만들었다고 생각하면 되며 지침 같은 표준이 없기 때문에 REST 방식의 URI 같은 경우 많이 살펴보면 공통점이 존재하는데, REST에서 쓰이는 일종의 관례라고 생각하자.

> reference

[https://meetup.toast.com/posts/92](https://meetup.toast.com/posts/92)

[https://www.youtube.com/watch?v=ETdbm5jDDsg](https://www.youtube.com/watch?v=ETdbm5jDDsg)