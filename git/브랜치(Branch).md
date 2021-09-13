# 브랜치(Branch)

## 들어가기에 앞서..

우리가 소프트웨어를 개발할 때 개발자들은 동일한 소스코드를 함께 공유하고 다루게 된다. 동일한 소스코드 위에서 어떤 개발자는 버그를 수정하기도 하고 또 다른 개발자는 새로운 기능을 만들기도 한다. 이와 같이 여러 사람이 동일한 소스코드를 기반으로 서로 다른 작업을 할 때에는 각각 서로 다른 버전의 코드가 만들어 질 수 밖에없다.

이럴 때, 여러 개발자들이 동시에 다양한 작업을 할 수 있게 만들어 주는 기능이 바로 '브랜치(Branch)'이다.

각자 독립적인 작업 영역(저장소) 안에서 마음대로 소스코드를 변경할 수 있다. 어떻게 분리된 작업 영역에서 변경된 내용은 나중에 원래의 버전과 비교해서 하나의 새로운 버전으로 만들어 낼 수 있다.

## 브랜치(branch)란?

브랜치란 독립적으로 어떤 작업을 진행하기 위한 개념이다. 필요에 의해 만들어지는 각각의 브랜치는 다른 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행할 수 있다.

![https://blog.kakaocdn.net/dn/wgWGr/btreY4m7zR7/eXPm83WusWA0KimGC946Ck/img.png](https://blog.kakaocdn.net/dn/wgWGr/btreY4m7zR7/eXPm83WusWA0KimGC946Ck/img.png)

각각의 브랜치로 공통된 프로젝트에 여러 작업을 동시에 할 수 있다.

또한 이렇게 만들어진 브랜치는 다른 브랜치와 병합(Merge)함으로써, 작업한 내용을 다시 새로운 하나의 브랜치로 모을 수 있다.

여러 명이서 동시에 작업을 할 때에 다른 사람의 작업에 영향을 주거나 받지 않도록, 먼저 메인 브랜치에서 자신의 작업 전용 브랜치를 만들게 되는데, 각자 작업을 진행한 후, 작업이 끝난 사람은 메인 브랜치에 자신의 브랜치의 변경 사항을 적용한다. 이러한 방식으로 작업할 경우 '작업 단위', 즉 브랜치로 그 작업의 기록을 중간 중간에 남기게 되므로 문제가 발생했을 경우 원인이 되는 작업을 찾아내거나 그에 따른 대책을 세우기 쉬워진다.

![https://blog.kakaocdn.net/dn/ZoUQB/btreQ8RRAiH/oZoKfkrEcB4RS91z9H7zHk/img.png](https://blog.kakaocdn.net/dn/ZoUQB/btreQ8RRAiH/oZoKfkrEcB4RS91z9H7zHk/img.png)

브랜치를 사용하여 동시에 여러 작업을 진행할 때의 작업 흐름을 한눈에 파악할 수 있다.

## master 브랜치

저장소를 새로 만들면, Git은 바로 'master'라는 이름의 브랜치를 만들어 준다.

새로운 저장소에 새로운 파일을 추가 한다거나 추가한 파일의 내용을 변경하여 그 내용을 저장(커밋, Commit)하는 것은 모두 'master' 라는 이름의 브랜치를 통해 처리할 수 있는 일이 된다.

이때, 'master'가 아닌 또 다른 새로운 브랜치를 만들어서 '이제부터 이 브랜치를 사용할거야!'라고 선언(체크아웃, checkout)하지 않는 이상, 이 때의 모든 작업은 'master' 브랜치에서 이루어 집니다.

![https://blog.kakaocdn.net/dn/bTvLxs/btreXpS7pko/HCFAdpWwQ8eLutFBG12EkK/img.png](https://blog.kakaocdn.net/dn/bTvLxs/btreXpS7pko/HCFAdpWwQ8eLutFBG12EkK/img.png)

새로운 브랜치를 만들지 않으면 모든 작업은 master 브랜치에서 이루어진다.