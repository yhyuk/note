# 변경 이력 병합(Merge)하기

병합을 의미하는 Merge를 통해 git에서 다른 브랜치와 병합할 수 있다. 주의할 점은 '현재' 브랜치에서 변경하는 점이다.

만약 내가 끌어온 저장소가 최신 버전이 아닌 경우, 즉 내가 pull 을 실행한 후 다른 사람이 push 를 하여 원격 저장소를 업데이트 해버린 경우에는 위의 그림과 같이 내 push 요청이 거부된다.

![https://blog.kakaocdn.net/dn/bL92aU/btreOs2Cyxq/4MKvNWqfABe0N8M5y3jXfk/img.png](https://blog.kakaocdn.net/dn/bL92aU/btreOs2Cyxq/4MKvNWqfABe0N8M5y3jXfk/img.png)

내 PC에 pull -> 다른 사람이 원격저장소에 push(업데이트) -> 나의 push는 거부된다.

위 그림 처럼 기존에 원격 저장소에 있던 파일을 내가 pull하며 작업을 끝낸 후 다시 push하려 할 때 다른 사람이 이미 push를 했다면 기존 파일과 충돌이 나므로 이런경우에는 병합(merge)이라는 작업을 진행하여 다른 사람의 업데이트 이력을 내 저장소에도 갱신 해야한다. 만약 병합하지 않은 채로 이력을 덮어쓰게 되면 다른 사람이 push 한 업데이트 내역(아래 그림의 커밋C)이 사라져 버리기 때문이다.

![https://blog.kakaocdn.net/dn/LSXbO/btreLKvVXgI/sKLeFpGkuFpCYnxAkouIvK/img.png](https://blog.kakaocdn.net/dn/LSXbO/btreLKvVXgI/sKLeFpGkuFpCYnxAkouIvK/img.png)

나의 파일과 다른사람의 파일이 충돌나는 상황에서 merge(병합)을 통해 해결할 수 있다.

정리하자면, git merge의 기능은 git이 현재 브랜치에 알아서 변경사항(다른 사람의 작업내용)을 통합해 주는 것이다!