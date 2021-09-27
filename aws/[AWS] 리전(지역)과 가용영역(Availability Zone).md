# [AWS] 리전(지역)과 가용영역(Availability Zone)

## **[AWS] 리전(지역)과 가용영역(Availability Zone)**

### **1. 리전(지역) 이란?**

- 말 그대로 지리적 위치를 말한다. (아마존 웹 서비스들의 서버가 어디에 위치 하는지 생각해보자.)
- 내가 서비스 하려는 지역의 주 고객들이 거주하는 지역과 서버의 거리가 멀면 멀수록 느려진다. (웹 사이트를 운영한다고 하면 내 싸이트를 이용하는 고객이 어디에 위치하는지에 따라 중요하다)
- 즉 주 고객들이 거주하고 있는 곳과 가까운 리전을 사용하는 것이 당연히 좋다.
- 최소한 2개이상의 가용 영역(AZ)로 구성된다.
- 2019년 2월 기준 20개의를 리전

### **2. 가용영역(Availability Zone)**

### **● 데이터센터의 클러스터**

- 한 리전에는 여러 가용성 영역이 있다 (한 리전당 최소 2AZ)
- 전용선으로 연결 되어 있기 때문에 마친 한 건물인 것과 같이 빠르게 데이터를 주고 받을 수 있다. (데이터 센터의 클러스터)
- 그렇기 때문에 빠르게 데이터를 백어 하고 데이터를 이전할 수 있는 구조이다.

### **● 다른 가용영역(AZ)의 장애로부터 격리됨**

- **각각의 다른 가용 영역의 장애로부터 격리될 수 있다는 점**이 중요하다.

- 자연재해 또는 단층선에 문제가 발생할 수 있는 곳은 AWS에서 가용영역을 분리한다.(리전의 AZ들은 지연시간이 짧은 링크를 통해 연결되어 있다.)

- 좀더 쉽게 예를 들어 설명하자면 하나의 지역에 혹시 특정 서비스들 이용할 수 있는 하나의 건물이 있다고 생각 해보자. 혹시 이 건물이 자연재해로 인해 (지진 등) 건물이 부서진다고 하면 아무 서비스를 이용할 수 없을 것이다. 똑같은 서비스를 타지역의 다른 건물에서 서비스 하고있다면 일단 해당 건물을 통해 서비스는 가능 한 것이다. 즉, 현재 서울의 AZ는 2개이고 한개의 AZ가 장애가 나더라도 다른 AZ를 통해 서비스가 가능한 구조이다. **이런 위험 분산 측면에서 AZ가 최소한 2개이상으로 구성되어 있는 것 같다.**

![https://blog.kakaocdn.net/dn/ezucMk/btrgbK2bzG6/RQ9euHywCKCc96D6XaDLt1/img.png](https://blog.kakaocdn.net/dn/ezucMk/btrgbK2bzG6/RQ9euHywCKCc96D6XaDLt1/img.png)

### **3. 리전지역과 가용영역의 사례 예시**

> 예시)2019년 11월 22일 AWS의 서울 지역 서버에 장애가 발생하였다. 당시 장애는 비록 오전 시간 약 84분간 발생하였고, 배달의민족, 쿠팡, 야놀자, 마켓컬리, 여러 암호화폐거래소, 신한은행 등의 사업자와 일반 사용자들이 크고 작은 불편을 겪었다.

- 이 기업들의 공통점은 **서울 리전에만 AWS를 구축해놓은 기업 들**이다.
- 이 당시 대안으로 얘기가 나왔던 것이 **멀티클라우드** 이다. (일본 등 다른 지역의 AWS 리전으로 멀티 클라우드를 적용한 기업들은 이번 장애를 피할 수 있었기 때문이다.)
- AWS와 기업들은 **SLA(서비스레벨어그리먼트) 99.95%** 서비스 수준 계약을 체결 한다.(**SLA 99.95%란** 한 달에 4시간 이상 서비스 장애가 발생해야만 보상을 제공한다는 내용) 어찌보면 고객에게 불리할 수 있는 조항이다. 또 앞으로도 장애가 발생하지 않는다는 보장도 없다.

정말 단 1분 1초도 서비스가 중지되는 사태를 멀티클라우드를 통해 피해 갈 수 있을 것으로 생각 되지만, 비용문제도 있을 수 있으니 신중히 접근하도록 해야 할 것 같다.

AWS 구축시 한번쯤 고려해 볼 만한 사항이다.

> Reference

[https://aws.amazon.com/ko/about-aws/global-infrastructure/regional-product-services/](https://aws.amazon.com/ko/about-aws/global-infrastructure/regional-product-services/)

[https://aws.amazon.com/ko/about-aws/global-infrastructure/regions_az/](https://aws.amazon.com/ko/about-aws/global-infrastructure/regions_az/)

[https://goddaehee.tistory.com/178](https://goddaehee.tistory.com/178)

[https://www.cloudping.info/](https://www.cloudping.info/)