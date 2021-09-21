# EC2 (Elastic Compute Cloud)

**정의**

독립된 컴퓨터를 임대해주는 서비스 (AWS의 대표적인 서비스, 대표적인 상품)

**특징**

- 컴퓨터 요구사항의 변화에 따라 컴퓨팅 파워를 조정할 수 있다.
- 새로운 서버 인스턴스 확보 및 부팅시간을 몇분으로 단축시킬 수 있다.
- 실제로 사용한 용량만큼만 지불 가능 (요금제 선택에 따라 낭비할 수 도 있음)
- Linux / Windows 중 선택 가능하다 (이외 운영체제는 현재 지원 X)
- 안정성을 위해 여러 AWS 리전과 가용 영역에 걸쳐 배포한다.

## **EC2 시작하기**

**STEP 시작 전... 사전작업**

- 우측 상단에 위치한 리전(지역)을 서울로 선택하자.

![https://blog.kakaocdn.net/dn/bf6bT6/btrfDhfehQk/47KaSHPHmuotBahcH22Ba1/img.png](https://blog.kakaocdn.net/dn/bf6bT6/btrfDhfehQk/47KaSHPHmuotBahcH22Ba1/img.png)

- 모든 서비스를 클릭 후 EC2 메뉴를 선택한다.

![https://blog.kakaocdn.net/dn/b1qC5c/btrfDgm4Tpb/jG0jCwptpsh7lssWQty0K0/img.png](https://blog.kakaocdn.net/dn/b1qC5c/btrfDgm4Tpb/jG0jCwptpsh7lssWQty0K0/img.png)

- 접속 후 좌측 메뉴바에 있는 인스턴스를 클릭 후 인스턴스 시작을 누른다.

![https://blog.kakaocdn.net/dn/b6dUNJ/btrfG3Hu6FF/UyVhS2nzksFe7ah4oR1LBK/img.png](https://blog.kakaocdn.net/dn/b6dUNJ/btrfG3Hu6FF/UyVhS2nzksFe7ah4oR1LBK/img.png)

**STEP1. Amazon Machine Image(AMI) 선택하기**

![https://blog.kakaocdn.net/dn/pW54s/btrfzj5Hg1C/kNUrakg75n7M0MrV80FV7K/img.png](https://blog.kakaocdn.net/dn/pW54s/btrfzj5Hg1C/kNUrakg75n7M0MrV80FV7K/img.png)

- Amazon Machine Image(AMI) 선택 이라고 하는 것은 **운영체제를 선택**한다고 보면 된다.

* AMI : 사전 구성된 Amazon 머신이미지 라고 볼 수 있다.

- Linux / Windows 중에서 선택 가능하다.

*직접 리눅스를 커스터 마이징 하여 아마존 웹서비스에 최적화한 **Amazon Linux를 제공**한다.

- Windows같은 경우 [ Microsoft Windows Server 2019 Base ], [ Microsoft Windows Server 2019 Base with Containers], [Microsoft Windows Server 2016 Base] 등 프리티어 사용 가능 하다는 뱃지가 붙어 있어야 무료이다.

***SQL Server (Database) 가 제공되는 경우는 유료**이다. SQL Server는 매우 비싸기 때문에 유의 하자

- 저는 Amazon Linux를 사용해 보려고 합니다. (Amazon Linux AMI 2018.03.0 선택)

**STEP2. 인스턴스 유형 선택**

![https://blog.kakaocdn.net/dn/bqdTlZ/btrfw5mlx0y/mOkDZB1oTgWHWBXMXzX5c0/img.png](https://blog.kakaocdn.net/dn/bqdTlZ/btrfw5mlx0y/mOkDZB1oTgWHWBXMXzX5c0/img.png)

- [프리 티어 사용 가능] 이 붙지 않은 Instance는 컴퓨터를 시작하는 순간부터 **과금이 발생할 수 있다.**

- vCPUs : CPU의 개수 설정 부분 (vCPU : 가상화된 CPU)

- 인스턴스 그룹을 좀더 살펴보자. 스크롤을 내려 보자.

![https://blog.kakaocdn.net/dn/cuEXbM/btrfFEVwqh4/rx2aR3tAV8qqz1KFWXQzq0/img.png](https://blog.kakaocdn.net/dn/cuEXbM/btrfFEVwqh4/rx2aR3tAV8qqz1KFWXQzq0/img.png)

[제목 없음](https://www.notion.so/9521f34ab38d4e62a6d692d3043b6e0a)

**STEP3. 인스턴스 세부 정보 구성**

![https://blog.kakaocdn.net/dn/cvjoEE/btrftn17BuC/4KE1zK31w4ucTLjf1PsanK/img.png](https://blog.kakaocdn.net/dn/cvjoEE/btrftn17BuC/4KE1zK31w4ucTLjf1PsanK/img.png)

- 인스턴스 개수 : Instance의 개수 설정 (몇 개까지 가 확장될 수 있는지 등)

- 구매 옵션 : 스팟 인스턴스란 AWS에서 유휴(놀고 있는, 사용하지 않는, 여유) 컴퓨터가 많은경우 할인 받을 수 있는 요금제라고 볼 수 있다.

- 종료 방식 : 중지 같은 경우 잠시 프리징 시킨다고 보면된다. 종료 같은경우는 아예 해당 Instance를 삭제한다고 보면 된다.

**STEP4. 스토리지 추가**

![https://blog.kakaocdn.net/dn/bwEUlR/btrfDg1F0x4/kziLeKCz9bmfleCkpwzsq1/img.png](https://blog.kakaocdn.net/dn/bwEUlR/btrfDg1F0x4/kziLeKCz9bmfleCkpwzsq1/img.png)

- 크기(GiB) : 메모리 GB

- 볼륨 유형 : SSD가 두 종류가 있는데, 프로비져닝된 IOPS SSD가 있는데 이는 직접 저장장치의 속도를 지정할 수 있다.

즉, 성능을 높게 잡으면 비용이 많이 발생할 수 있으니 난 범용 SSD를 선택 해야겠다.

- 종료 시 삭제 : 해당 옵션이 체크시 종료하면 컴퓨터와 저장장치가 모두 폐기된다고 보면된다. 체크가 안되있는 경우 컴퓨터는 폐기, 저장장치는 폐기되지 않는다고 보면 된다. ( 저장장치도 비용 발생할 수 있으니 체크 하고 넘어가도록 하자. )

**STEP5. 태그 추가**

![https://blog.kakaocdn.net/dn/mXbC8/btrfsc7DIGs/a3HbUIBmpORuiBgzNXNkgK/img.png](https://blog.kakaocdn.net/dn/mXbC8/btrfsc7DIGs/a3HbUIBmpORuiBgzNXNkgK/img.png)

- 어떤 인스턴스를 만들고, 어떤 용도, 누가 관리 하는지 등의 메모기능이라고 볼 수 있다.(설명 기능)

- 간단히 해당 EC2의 역할이 먼지만 기록하고 넘어가도록 하자. (해당 EC2 Instance의 이름만 지정하였다.)

**STEP6. 보안 그룹 구성**

![https://blog.kakaocdn.net/dn/k7i1E/btrfuPKMXLW/gYOkghkgYdnOEhFk1kUUcK/img.png](https://blog.kakaocdn.net/dn/k7i1E/btrfuPKMXLW/gYOkghkgYdnOEhFk1kUUcK/img.png)

- 권한과 관련된 것을 지정한다. (네트워크를 통해 누가 인스턴스에 접속 가능한지. 어떤 접속방식 허용할지 등의 보안설정 가능)

- Default는 SSH 접속 허용이다. (임의 지정하여 특정 IP만 허용가능, 계속 **[규칙추가]**하여 또 다른 IP도 추가 가능하다)

- 보안 그룹 할당: **[새 보안 그룹 생성]**하여 추후 새로 만들 서버들에게도 동시에 적용 가능하다

- Type을 추가 또는 제거 하여 내가 만든 Instance의 허용 접속 방법, 트로토콜을 허용 할 수 있다.

(**[소스]** => **[내 IP]** 를 선택 시 해당 웹 페이지 접속한 IP가 자동으로 선택 된다. 해당 IP만 허용, 위치무관은 누구나 접속 가능)

(리눅스계열의 원격제어 방식인 SSH, 웹 브라우저로 접속하는 경우 HTTP 또는 HTTPS)

- 나와 같은 경우는 SSH, HTTP 만 접속 허용하도록 설정하고 **[ 검토 및 시작 ]** 을 클릭하여 주었다.

**STEP7. 인스턴스 시작 검토**

![https://blog.kakaocdn.net/dn/c82ItP/btrfG2u4xCf/X87Om1DMezivCezbzsdpn1/img.png](https://blog.kakaocdn.net/dn/c82ItP/btrfG2u4xCf/X87Om1DMezivCezbzsdpn1/img.png)

- 최종 검토 페이지이다.

- 시작하기 클릭시 네트워크 시작시 지정할 비밀번호 설정 페이지가 호출된다.

![https://blog.kakaocdn.net/dn/bopagl/btrfElVTBvR/AceJvsUkxEKyLMZklB4kx0/img.png](https://blog.kakaocdn.net/dn/bopagl/btrfElVTBvR/AceJvsUkxEKyLMZklB4kx0/img.png)

- 단순한 비밀번호를 사용하면 해킹당할 위험이 크기 때문에 KeyPair를 제공하여 준다.

- 키 페어 다운로드를 클릭 후 다운받은 파일을 txt 파일로 열어본 결과

![https://blog.kakaocdn.net/dn/DXW0H/btrfBrWH5xX/aFcgRPvnrydG44fSQKDQOk/img.png](https://blog.kakaocdn.net/dn/DXW0H/btrfBrWH5xX/aFcgRPvnrydG44fSQKDQOk/img.png)

- [ 새 키페어 생성 ]을 선택하고 케피어 이름을 선택한 후 [ 키 페어 다운로드 ]를 클릭하면 다운로드 됨과 동시에 생성할 Instance에 비밀번호를 자동으로 설정하여 둔다.

- 해당 키 페어는 절대 다시 발급해주지 않기 때문에 중요하다.

- **키 페어를 어디에 저장해야 할까?**
- AWS 자습서에서는 다음 위치에 저장 할 것을 권고, 가이드 하고 있다.

(참고 [https://aws.amazon.com/ko/getting-started/tutorials/launch-a-virtual-machine/](https://aws.amazon.com/ko/getting-started/tutorials/launch-a-virtual-machine/))

**1. Windows 사용자**

- 키 페어를 .ssh라는 하위 디렉터리에 있는 사용자 디렉터리에 저장하는 것이 좋다.

(ex: C:\user\{yourusername}\.ssh\MyKeyPair.pem).

(팁: .ssh 라고 폴더를 생성시 오류가 발생 한다

![https://blog.kakaocdn.net/dn/thcX7/btrfBsahuu5/3a83GoMIiQVYjJHkfkpUEK/img.png](https://blog.kakaocdn.net/dn/thcX7/btrfBsahuu5/3a83GoMIiQVYjJHkfkpUEK/img.png)

.ssh.라고 폴더 이름을 입력하면 마지막에 있는 마침표가 자동으로 제거된다.

![https://blog.kakaocdn.net/dn/bPcr9P/btrfsedjGgR/kJHmhIPIZrVkQFtZGGImIK/img.png](https://blog.kakaocdn.net/dn/bPcr9P/btrfsedjGgR/kJHmhIPIZrVkQFtZGGImIK/img.png)

**2. Mac/Linux 사용자**

- 키 페어를 홈 디렉터리의 .ssh 하위 디렉터리에 저장하는 것이 좋다

(ex: ~/.ssh/MyKeyPair.pem).

- 팁: MacOS에서는 기본적으로 키 페어가 다운로드 디렉터리에 다운로드 된다.

키 페어를 .ssh 하위 디렉터리로 이동하려면 터미널 창에 mv ~/Downloads/MyKeyPair.pem ~/.ssh/MyKeyPair.pem 명령을 입력한다.

**마무리**

- 키페어 저장이 끝났으면 [ 인스턴스 시작 ] 클릭. - 다음과 같이 시작 중이라는 상태 로그를 볼 수 있다.

![https://blog.kakaocdn.net/dn/bpvoKi/btrfuKPIZ3I/QxHvgBkcz9RQlzcoOldpCK/img.png](https://blog.kakaocdn.net/dn/bpvoKi/btrfuKPIZ3I/QxHvgBkcz9RQlzcoOldpCK/img.png)

- 다시 처음 인스턴스 페이지로 돌아가보면 인스턴스가 생성 되었고, 초기화 중인 것을 볼 수 있다.

![https://blog.kakaocdn.net/dn/bDg0xh/btrfG1Xe90C/X7K5UDBUKoRtfFLkcG2KX0/img.png](https://blog.kakaocdn.net/dn/bDg0xh/btrfG1Xe90C/X7K5UDBUKoRtfFLkcG2KX0/img.png)

- 몇 분 뒤 초기화가 끝나고 이로써 EC2 Instance 한개가 생성 완료 되었다. 즉, 내 리눅스 OS 클라우드 컴퓨터 세팅이 완료 되었다.

> reference

[https://opentutorials.org/course/2717](https://opentutorials.org/course/2717)

[https://aws.amazon.com/ko/getting-started/fundamentals-core-concepts/](https://aws.amazon.com/ko/getting-started/fundamentals-core-concepts/)

[https://goddaehee.tistory.com/174](https://goddaehee.tistory.com/174)