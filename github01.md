# Git/Github 기본 실습


- 실습 환경 : https://ide.goorm.io/

- 기본 명령어

```
$ ls # list segments, 파일의 목록 표시
$ cd # change directory
$ cd .. # 상위 디렉토리로 이동
$ cd {dir_name} # 하위 디렉토리로 이동
$ pwd # print working directory
$ mv # 파일명 변경 (또는 파일경로 이동)
$ touch {file_name} # 빈 파일 만들기
```

- `q` 또는 `ctrl + c` 로 나갈 수 있음
```
git log --oneline | wc -l # 해당 프로젝트의 수정 횟수
git shortlog -sn | nl # 해당 프로젝트는 누가 제일 많이 작업했나요?
git shortlog -sn -- mnist | nl # 특정 폴더 (msnit) 는 누가 제일 많이 작업했나요?
git shortlog --after=2018-01-01 -sn -- mnist | nl # 특정 폴더 (msnit) 는 최근에 (after 2018-01-01) 누가 제일 많이 작업했나요?
```

```
git shortlog -h | grep summary
>    -s, --summary         Suppress commit descriptions, only provides commit count
git shortlog -h | grep number
>    -n, --numbered        sort output according to the number of commits per author
```

```
git shortlog -sn | nl 
```

```
git log --oneline --no-merges
```

```
git show
```

```
 git show 6c8e2ba # 특정 커밋 상세 확인
```

```
commit 6c8e2bab4d45f2386929c83bb4480c18d2b660fd
Author: mattip <matti.picus@gmail.com>
Date:   Sun Jul 5 18:20:41 2020 +0300

    fix warnings and failures

diff --git a/dcgan/main.py b/dcgan/main.py
index 4467e32..96d1feb 100644
--- a/dcgan/main.py
+++ b/dcgan/main.py
@@ -224,7 +224,8 @@ for epoch in range(opt.niter):
         netD.zero_grad()
         real_cpu = data[0].to(device)
         batch_size = real_cpu.size(0)
-        label = torch.full((batch_size,), real_label, device=device)
+        label = torch.full((batch_size,), real_label,
+                           dtype=real_cpu.dtype, device=device)

         output = netD(real_cpu)
         errD_real = criterion(output, label)
diff --git a/fast_neural_style/download_saved_models.py b/fast_neural_style/download_saved_models.py
index 71454bc..691c2c0 100644
--- a/fast_neural_style/download_saved_models.py
+++ b/fast_neural_style/download_saved_models.py

(more)
```


```
git show 6c8e2ba | grep "diff --git" | wc -l
> 4 # 해당 커밋은 4개의 파일을 수정한 이력이다. (commit 1개가 여러 개의 파일을 수정한 이력일 수 있다!)
```

```
git show --oneline # merge pull request commit id (맞는 표현인가?) 가져와서 확인해보자
git show 113447f
git log --oneline --no-merges
git log --oneline --no-merges | wc -l
```

```
git log -p # -p : 세부적으로 볼 수 있는 옵션
```

```
git log --oneline -- mnist # 특정 폴더의 log 출력 (오픈소스 기여할 때 집중할 폴더)
```

```
git log --oneline --after=2020-06-01 --before=2020-06-30 | wc -l
> 5
```
- wc : words count
- l : line

```
git log --oneline --reverse | head -3
> 23933fc Add MNIST example
> 3de8643 python 2.7 compatibility
> 7188625 add readme
```

```
git show 23933fc
commit 23933fcb49b33cfc7e2737b6b94bd329396c7d58
Author: Adam Paszke <adam.paszke@gmail.com>
Date:   Tue Aug 23 20:38:51 2016 -0700

    Add MNIST example
```
```
git show 3de8643
commit 3de8643a6072da24f0fd050ae05c99f66ecafa11
Author: soumith <soumith@gmail.com>
Date:   Wed Aug 24 09:01:16 2016 -0400

    python 2.7 compatibility

```

```
git log --oneline | nl
>     1  b3600fd Merge pull request #668 from gentlelinuxer/master
>     2  783f786 PR test
>     3  113447f Merge pull request #632 from gentlelinuxer/pr_test
>     4  5745995 PR test
```

```
git show b3600fd
commit b3600fd30f0968608918be6f6bd6547d10ed075a (HEAD -> master, origin/master, origin/HEAD)
Merge: 113447f 783f786
Author: Taeung Song <treeze.taeung@gmail.com>
Date:   Tue Jun 7 15:23:33 2022 +0900

    Merge pull request #668 from gentlelinuxer/master

    PR test
```
```
git show 783f786
commit 783f7862f8d1b5c9e71676c3e0ea700409f145ff
Author: Taeung Song <taeung@reallinux.co.kr>
Date:   Tue Jun 7 06:19:40 2022 +0000

    PR test
```
