# EC2 리눅스 인스턴스 접속하기

자! 이전에는 EC2에 대해서 알아보면서 설치까지 완료 하였다. 오늘은 설치한 해당 인스턴스에 어떤식으로 접속하는지 알아보자.

### **리눅스는 SSH 방식을 통해 원격 제어를 한다.**

- 윈도우는 SSH가 없기 때문에 ssh역할을 해줄 수 있는 프로그램을 설치해 줘야한다. (이 중 무료이면서 가장 대표인 것이 putty이다.)
- 저는 현재 사용하고있는 PC가 mac 기준이므로 터미널을 사용해서 접속하려고 합니다.
- 상세 설명을 보려면 다음과 같이 Instance 설정 화면에서 우클릭, **[연결]** 클릭 시 볼 수 있다.

![https://blog.kakaocdn.net/dn/rurc2/btrfuQi3lbw/Sxw6yhVFX9r9uJ2LevEuHk/img.png](https://blog.kakaocdn.net/dn/rurc2/btrfuQi3lbw/Sxw6yhVFX9r9uJ2LevEuHk/img.png)

- 클릭하게 되면 다음과 같이 확인 할 수 있다.

![https://blog.kakaocdn.net/dn/bvmfPj/btrfxPctW7r/zwP3IrLsOxt8vVkXEAkUdK/img.png](https://blog.kakaocdn.net/dn/bvmfPj/btrfxPctW7r/zwP3IrLsOxt8vVkXEAkUdK/img.png)

### **터미널 실행하기**

1. 어제 EC2 설치하면서 다운받은 키페어.pem 파일 경로로 이동한다. ( cd /경로 )

2. chmod 400 키 페어 이름.pem 입력한다.

3. 위 AWS 웹 브라우저에서 확인한 4번 메뉴의 명령어를 복사한 뒤 입력한다.

4. 그 이후 yes를 입력한다.

5. 마지막으로 인스턴스 환영 문구가 나온다면 AWS Linux 가상머신에 연결된 것이다!

![https://blog.kakaocdn.net/dn/beBBjF/btrfBrv4MEn/skufFHr8p4lZfKfhzhaVYk/img.png](https://blog.kakaocdn.net/dn/beBBjF/btrfBrv4MEn/skufFHr8p4lZfKfhzhaVYk/img.png)