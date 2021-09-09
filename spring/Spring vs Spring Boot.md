# Spring vs Spring Boot

우리가 흔히 알고 있는 자바 기반 대표적인 프레임워크인 Spring Framework와 Spring에서 불편한점 들을 고치고자 태어난 Spring Boot의 차이점을 알아보자.

[ Spring ]

먼저 Spring Framework란 무엇인가? Spring 홈페이지에서 소개글 중 핵심적인 문단을 한국어로 번역하자면 이렇다.

"Spring은 어떤 종류의 배포 플랫폼에서도 최신 자바 기반 기업용 애플리케이션을 위한 종합적인 프로그래밍 및 구성 모델을 제공해준다."

"Spring의 핵심 요소는 애플리케이션 수준에서의 인프라 자원이다. Spring은 기업용 애플리케이션의 plumbing에 초점을 맞춰 팀이 특정 배포 환경과 불필요한 시도없이 애플리케이션 수준의 비지니스 로직에 집중할 수 있게 해준다."

즉, Spring Framework는 객체 지향의 특징을 잘 활용할 수 있게 해주며, 개발자들은 핵심 비지니스 로직 구현에만 집중할 수 있게 해주는 프레임워크이다.

[ Spring Boot ]

Spring과 마찬가지로 홈페이지에서 핵심적인 문구를 번역하자면 이렇다.

"Spring Boot는 독립적이며, 운영할 수 있는 수준의 Spring 기반 애플리케이션을 쉽게 만들 수 있게 해준다. 그냥 실행해라."

"최소한의 설정으로 Spring 플랫폼과 서드 파티 라이브러리를 사용할 수 있다. 대부분 Spring Boot 애플리케이션은 최소한의 Spring 설정을 필요로 한다."

즉, Spring Boot를 통해 Spring 애플리케이션을 쉽게 만들 수 있게 해준다.

[ Spring vs Spring Boot ]

1. 의존성 관리

- Spring은 개발에 필요한 모듈의 의존성을 각각 다운 받아 줘야 했으며, 각 모듈의 버전을 개발자가 하나하나 명시해줘야 했다.
- Spring Boot는 "spring-boot-starter"를 지원해준다. 자주 사용하게 되는 모듈간의 의존성과 버전 조합을 제공해준다.

2. 자동 설정

- Spring은 많은 환경 설정이 필요하다.
- Spring Boot는 application.yml(및 properties)등 에서 간단히 설정만 하면 DB에 연결이 가능하다.
- Spring Boot에서 제공하는 어노테이션을 통해 설정 작업이 편리해진다.
- Spring Boot는 Classpath에 라이브러리 jar 파일이 등록 되면 spring.factories에 있는 관련설정이 실행되며, 자동 설정 후보 클래스의 @Conditional~ 조건에 따라 bean 으로 등록된다.
- spring-configuration-metadata는 자동 설정에 사용할 프로퍼티 정의 파일로, application.yml(및 properties)에 작성한 값으로 프로퍼티를 세팅한 후, 구현되어 있는 자동 설정에 값을 주입 시켜준다.

3. 내장 WAS(Web Application Server)

- Spring을 통해 웹을 개발하고 난 후 배포 하려면 애플리케이션 war 패키징 -> WAS 설치(Tomcat, Undertow, Jetty) -> WAS에 WAR파일 올리기 순으로 되기 때문에 번거롭다.
- Spring Boot는 WAS가 내장되어 있다.(독립적으로 실행이 가능하도록 SpringBootTestApplication 내장 서버가 있다.)

4. 모니터링

- Spring Boot의 모듈 중 하나인 "Actuator"는 애플리케이션의 관리 및 모니터링을 지원해준다. Actuator는 사용 서비스 수준에서 필요로 할 모니터링 기능을 엔드포인트로 미리 만들어서 제공해준다.

* 주의 사항

-> Actuator는 민감한 정보도 많이 제공되기 때문에 운영 시에는 Spring Security등을 이용하여 보안에 신경을 써야한다.

-> Actuator의 데이터를 영구 저장소에 저장해주지 않으면 없어질 수 있다.

[ 차이점 정리 ]

Spring은 Spring Framework를 기반으로 여러 서브 프로젝트들의 모음으로 이루어져 있으며, 서브 프로젝트들은 여러 모듈을 가지고 있다. 개발할 애플리케이션에 맞게 여러 모듈들을 조합해서 사용한다.

Spring Boot도 Spring 프로젝트 중 하나로, Spring Framework와 별개로 사용할 수 없으며, Spring을 편하게 사용하게 해주는 역할이며 크게 장점으로 4가지를 꼽자면, 첫번째) 의존성 관리, 두번째) 자동 설정, 세번째) 내장 WAS, 네번째) 모니터링 등이 있다.

[ 참고 자료 ]

[https://www.youtube.com/watch?v=Y11h-NUmNXI&ab_channel=%EC%9A%B0%EC%95%84%ED%95%9CTech](https://www.youtube.com/watch?v=Y11h-NUmNXI&ab_channel=%EC%9A%B0%EC%95%84%ED%95%9CTech)

[https://msyu1207.tistory.com/entry/Spring-VS-Spring-Boot-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%84-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90](https://msyu1207.tistory.com/entry/Spring-VS-Spring-Boot-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%84-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)