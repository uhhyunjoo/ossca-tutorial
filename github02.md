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
