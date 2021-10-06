# 메이븐(Maven) vs 그래들(Gradle)

# **메이븐(Maven) vs 그래들(Gradle)**

기존에 메이븐(Maven)은 자바를 사용한 프로젝트에서 쓰는 것 이라는 추상적으로 알고 있었는데, 규모에 따라 프로젝트에서 사용하는 메이븐 같은 관리도구가 그래들(Gradle)이라는 관리도구도 사용한다는 것을 알게되어서 직접 공부한 내용을 정리해보려 합니다.

### **Maven 이란?**

- 아파치에서 제공하는 메이븐은 **자바용 프로젝트 관리 도구** 이다.
- 아파치 앤트의 불편함을 해결하고자 만들었으며, 프로젝트를 진행하면서 사용할 수 많은 라이브러리들을 관리해주는 도구이다.

### **Maven의 장점 및 특징**

- 라이브러리들과 연관된 라이브러리까지 거미줄 처럼 다 연동 되어서 관리가 된다.
- pom.xml을 이용한 정형화된 빌드 시스템(필요한 라이브러리를 정의 해두면 알아서 **네트워크를 통하여 자동으로 다운로드**를 해준다.)
- 간단한 설정을 통한 배포 관리가 가능하다.

### **Maven의 pom.xml 예시**

```html
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>

   <groupId>com.example</groupId>
   <artifactId>demo-maven</artifactId>
   <version>0.0.1-SNAPSHOT</version>
   <packaging>jar</packaging>

   <name>demo-maven</name>
   <description>Demo project for Spring Boot</description>

   <parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>1.5.4.RELEASE</version>
      <relativePath/> <!-- lookup parent from repository -->
   </parent>

   <properties>
      <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
      <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
      <java.version>1.8</java.version>
   </properties>

   <dependencies>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter</artifactId>
      </dependency>

      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-test</artifactId>
         <scope>test</scope>
      </dependency>
   </dependencies>

   <build>
      <plugins>
         <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
         </plugin>
      </plugins>
   </build>

</project
```

### **Gradle 이란?**

- 그래들은 **Groovy를 이용한 빌드 자동화 시스템**이다.
- Groovy와 유사한 도메인 언어를 채용하였으며, 현재 안드로이드 앱을 만드는데 필요한 안드로이드 스튜디오의 공식 빌드 시스템이기도 하다.
- Java, C/C++, Python 등과 같은 여러 가지 언어를 지원한다.

### **Gradle의 장점 및 특징**

- Maven과 Ant의 장점을 조합하여 만든 빌드 도구이다.
- ***build.gradle**을 이용한 정형화된 빌드 시스템이다. (*build.gradle: 메이븐의 pom.xml과 비슷한 플러그인, 의존성 추가를 위한 파일이다.)
- 멀티 프로젝트에 용이하다.

### **Gradle의 build.gradle 예시**

```html
buildscript {
    ext {
        springBootVersion = '1.5.4.RELEASE'
    }
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
}

apply plugin: 'java'
apply plugin: 'idea'
apply plugin: 'org.springframework.boot'

version = '0.0.1-SNAPSHOT'
sourceCompatibility = 1.8

repositories {
    mavenCentral()
}

dependencies {
    compile('org.springframework.boot:spring-boot-starter')
    testCompile('org.springframework.boot:spring-boot-starter-test')
}
```

### **Maven vs Gradle**

Gradle이 **시기적으로 늦게 나온만큼 사용성, 성능 등 비교적 뛰어난 스펙**을 가지고있다.

Maven보다 Gradle이 좋은점은 아래와 같다.

1. Build라는 동적인 요소를 XML로 정의하기에는 어려운 부분이 많다.
    - 설정 내용이 길어지고 가독성 떨어짐
    - 의존관계가 복잡한 프로젝트 설정하기에 부적절하다.
    - **상속구조를 이용한 멀티 모듈 구현**
    - 특정 설정을 소수의 모듈에서 공유하기 위해서는 부모 프로젝트를 생성하여 상속하게 해야 함 (상속의 단점 생김)
2. Gradle은 Groovy를 사용하기 때문에, 동적인 빌드는 Groovy 스크립트로 **플러그인을 호출하거나 직접 코드를 짜면 된다.**
    - Configuration Injection 방식을 사용해서 공통 모듈을 상속해서 사용하는 단점을 커버했다.
    - 설정 주입 시 프로젝트의 조건을 체크할 수 있어서 프로젝트별로 주입되는 설정을 다르게 할 수 있다.

### **결론**

- 현재는 분명히 Maven의 점유율이 더 높고 익숙한 사람이 많은 상황이지만, Gradle의 추격이 더 빨라지고 있어서 조만간 상황이 역전될 가능성이 더 높다고 하는 사람이 많아 지고 있다.
- Gradle이 조금 더 빠른 성능과 간결한 설정의 매력을 보유하고 있어 인기도가 상승 중이며, 소규모 프로젝트에서는 큰 차이가 없어서 익숙한 Maven을 사용해도 무방하지만 규모가 커질수록 Gradle을 사용하는 것이 체감상 더욱 유리하다고 한다.
- gradle 의 빌드 스크립트는 groovy 라는 언어로 작성해야 하므로 maven 의 xml 에 비하면 친숙하진 않지만 확장성이 뛰어나다.
- maven 은 프로젝트가 커질수록 빌드 스크립트의 내용이 길어지고 가독성이 떨어지는 반면, gradle 은 훨씬 적은 양의 스크립트로 짧고 간결하게 작성할 수 있다.
- maven 의 경우 멀티 프로젝트에서 특정 설정을 다른 모듈에서 사용하려면 상속을 받아야 하지만 **gradle 은 설정 주입 방식**으로 이를 해결한다.
- gradle 은 **멀티 프로젝트에 매우 적합**하며, 빌드 속도는 다양한 시나리오 상에서 **10~100배 가량이 빠르다.**

> reference
> 

[https://gradle.org/maven-vs-gradle/](https://gradle.org/maven-vs-gradle/)

[https://mylupin.tistory.com/39#recentComments](https://mylupin.tistory.com/39#recentComments)

[https://okky.tistory.com/179](https://okky.tistory.com/179)

[http://dawoonjeong.com/spring-maven-vs-gradle/](http://dawoonjeong.com/spring-maven-vs-gradle/)