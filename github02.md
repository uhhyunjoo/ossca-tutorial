## git stash
- 개발하는 과정에서 언제 쓰일까?
ex. 버그 수정 : before / after 테스트 점검
  - stash 를 이용하여 임시저장을 한다. -> 원상복귀 -> before 테스트 -> stash pop 으로 복구 -> after 테스트

```
git dff
git status
git stash
git status
git stash pop
git stash
```

- stash (수정 내용 저장) 와 checkout (파일복구)의 공통점은?
- 결과적으로 원상복구ㅇㅇ

  - checkout 명령어 : ex. 도서관에서 책을 대출 받을 때 == .git 이라는 히스토리 창고에서 파일을 가져오는 것과 유사한 개념 


```
nano mnist/main.py # 수정
git add mnist/main.py
git status
git reset
git status
```

- commit 취소

```
git log --oneline -3
git reset --hard HEAD~1
git log --oneline -3
```

![image](https://user-images.githubusercontent.com/41139770/179341456-576ac60d-c85b-4058-83cf-100f4567f0e1.png)

- commit 생성할 때 `-s` 옵션을 넣는 이유?
- `Signed-off-by` 가 추가된다.
- Author 정보가 있는데, 굳이 이걸 넣는 이유??? -> 라이센스 서명 절차... 라이센스에 동의했다는 서명 절차라고 합니당
- 오픈소스 작업할 때는 `CLA` 절차를 받아서, 따로 `signed-off-by` 를 넣지 않아도 된다고 한다...~
![image](https://user-images.githubusercontent.com/41139770/179341556-6ea34df4-523c-43d1-858b-3ba114923172.png)

- [tensorflow 구경](https://github.com/tensorflow/tensorflow/pulls?q=label%3A%22cla%3A+no%22+)

![image](https://user-images.githubusercontent.com/41139770/179341678-7ddf7d4c-6772-443e-a417-93795fa26147.png)

- 기존의 commit 을 수정한다. (가장 최신 commit 을 수정한다.)
- rewind 되감기 기능 -> 중간의 commit 도 수정은 가능하다

```
git commit --amend
```

- 다른 사람의 작업이 먼저 merge 된 경우
- maintainer 가 내 PR예 댓글로 `plz rebase` 라고 할 것이다. (내꺼 merge 하려고 할 때 ㅇㅇㅇ)
- rebase 라는 용어 자체를 `rebase` 명령어 자체로 생각하지 말고, 보다 포괄적인 의미로 생각해야한다.
- rebase == 베이스 업데이트

- 프로젝트 운영자 vs 프로젝트 참여자 : 이 입장에서, rebase 를 다르게 고려한다.
- 운영자 : rebase 라는 것을 관점으로, 어떻게 운영할까
- 참여자 : 입장에서는 base 가 바뀐다는 개념을 알고 있어야한다.
  - 그래서, upstream 을 remote 로 추가했던 것임 ㅇㅇ


```
git fetch upstream master # upstream/master 내부 브랜치 자동 생성됨
git rebase upstream/master # 1단계-2단계-3단계 한 번에 실행된다
git rebase =i , ==interactive # 되감기 기능
```

- git history == commit (블록) 들이 쌓인다.

- 10 개의 commit 을 제출했는데, 리뷰 받았을떄...
  - 1번 commit 은 버리고, 2번 commit 은 너무 크니까 여러 개로 쪼개고 ... 그렇게해주세용
  - 오픈소스 == 협업이 본질 == `git rebase -i` 가 필요할 것임~ (초보 떄는 말고 ㅇㅇ)
