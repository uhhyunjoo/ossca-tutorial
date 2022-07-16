
```
git rebase -i --root
git rebase -i HEAD~10 # 최신부터 10개까지의 범위에서 rebase interactive 작업을 할것이다.
```
- pick 을 edit 으로 수정

```
git rebase --continue # 감았던걸 펴는 작업
```

![image](https://user-images.githubusercontent.com/41139770/179342770-78633a52-50fb-4228-b2e2-4fb96e5a9ca1.png)

![image](https://user-images.githubusercontent.com/41139770/179342824-5a425de7-c292-4679-8992-a85ae86b4801.png)

![image](https://user-images.githubusercontent.com/41139770/179342836-8cd5b72a-24c3-4f68-875d-a808cd12a827.png)

![image](https://user-images.githubusercontent.com/41139770/179342851-84d0164c-0506-46cc-880a-d8e3401062c2.png)


![image](https://user-images.githubusercontent.com/41139770/179342909-4fc24d22-09a3-469c-a026-f699bf0a9e52.png)

- 가장 옛날의 두번째만 남겨놓고 되감아주는 것임~

```
touch hello_1.c && git add hello_1.c && git commit -m 'Add hello_1.c' # 앞 명령어가 안되면 뒤에도 실행 안된다~
```

![image](https://user-images.githubusercontent.com/41139770/179343093-f33f0c55-7c1f-4576-9b7c-aca6d45765a8.png)

![image](https://user-images.githubusercontent.com/41139770/179343172-74b80b45-a7da-4d44-8fa4-5c57361a6578.png)

![image](https://user-images.githubusercontent.com/41139770/179343210-0084e165-1129-41ac-a10d-d6e4069db574.png)

```
git reset --hard origin/master

```


```
git remote -v
git remote remove origin
git remote add origin https://github.com/alro923/git-training.git
git remote add upstream https://github.com/Taeung/git-training.git
```

```
git rebase -i --root # Add hello_3.c 까지만 살려주셈
git log --oneline
git reset --soft HEAD~1
```

![image](https://user-images.githubusercontent.com/41139770/179343669-7fd2c123-d70c-4bb6-af0b-6b85ea53ff19.png)

![image](https://user-images.githubusercontent.com/41139770/179343723-79c8efde-9b3b-44ea-a5fd-e0193f60f1e1.png)

![image](https://user-images.githubusercontent.com/41139770/179343790-b02596ba-b04b-4d38-a733-81bfb246eecf.png)

![image](https://user-images.githubusercontent.com/41139770/179343816-fb420611-02c1-4955-ac58-086741f33bb0.png)

![image](https://user-images.githubusercontent.com/41139770/179344018-438e67f3-6ec8-47ae-a61a-f25fb75b2518.png)

![image](https://user-images.githubusercontent.com/41139770/179344175-7d5019e3-9033-4479-951b-7b8e053d9f85.png)



- git blame


```
git blame src/node_http_parser.cc
```
- /class Parser : 로 검색
- 239번 줄...~

```
git show 7c4b09b24bb
git reset --hard 7c4b09b24bb~1
git blame src/node_http_parser.cc
```

- /class Parser
![image](https://user-images.githubusercontent.com/41139770/179345217-6f049618-e90d-4ffa-81c7-a97eb9c21e16.png)

![image](https://user-images.githubusercontent.com/41139770/179345156-99fe7177-a15f-43de-ba12-a82499adbc7d.png)

- 2016-02-19, 147 번 라인 : id 복사~
```
![image](https://user-images.githubusercontent.com/41139770/179345052-e6e45a78-a389-4baf-b4d4-d4007ca59ab9.png)
- 수정? 최초? -> 수정 커밋입니다~ (- + 니깐)

![image](https://user-images.githubusercontent.com/41139770/179345230-959e266a-87b8-4059-9a57-ab3f71bf58b5.png)


- 깃허브에서 보기
![image](https://user-images.githubusercontent.com/41139770/179345285-b8083485-4fe3-4405-9ab3-7f4f447c519a.png)

- `blame` 클릭

![image](https://user-images.githubusercontent.com/41139770/179345301-8fc3d54d-b9b4-4d20-b4ca-268cb1185c07.png)

![image](https://user-images.githubusercontent.com/41139770/179345355-f3c8df22-a86b-4764-ad79-d0356f21c672.png)

![image](https://user-images.githubusercontent.com/41139770/179345368-17c08d1b-cb95-4694-8662-58b71943c971.png)

```
$ git show 42ee169
```

![image](https://user-images.githubusercontent.com/41139770/179345409-5454cd42-0742-4696-8af8-bfdf9d4c3dab.png)


- 이 이미지를 보는 것만으로도 첫번째 커밋을 찾을 수 있다...(?어떻게?)
![image](https://user-images.githubusercontent.com/41139770/179345432-b5f9aa1b-b514-4125-b2ee-609911c6f2e8.png)

- cpp 에서 클래스 선언 -> 생성자 -> 함수 -> 중괄호(diff 에 잘 안잡힌다... 수정이 일어나도 잘 변경 안됨...~ 이건 약간 센스 같은? 거라고 함)

![image](https://user-images.githubusercontent.com/41139770/179345487-6cf309e5-6acc-4cee-8354-8b2064fc209f.png)
- 이건 추가 커밋임... 유감~

```
git log --oneline --reverse -- src/node_http_parser.cc | head -1
```
```
git log --oneline --reverse -- src/node.cc | head -1
```
- /class Parser

![image](https://user-images.githubusercontent.com/41139770/179345599-100d5eca-8431-48b4-b2df-3d4768eb7f94.png)

- 얼렐레...?

- `+` 천국이 아니네...? `-`가 있네...?
```
git reset --hard 1a126ed11c~1
```

![image](https://user-images.githubusercontent.com/41139770/179345649-0c64b153-52ff-4c50-8636-0912d2049285.png)

- 과거로 돌아가봤더니... `src` 폴더가 없다?? 그런데 `node.cc` 는 있다??
- 아 node.cc 가 원래 있었고, 이후에 src 폴더를 생성해서 node.cc 를 옮긴거구나~

```
git log --oneline --reverse -- node.cc | head -1

```

![image](https://user-images.githubusercontent.com/41139770/179345742-c745957b-bfbe-43a9-96a7-8c16b6624230.png)

- node 프로젝트가 처음 만들어질때 최초부터 commit 3개를 찾아라~
```
git log --oneline --reverse | head -3

```
![image](https://user-images.githubusercontent.com/41139770/179345828-1e0f004a-1a6f-4545-9e2b-7931ac14fcff.png)

> 끝...~ 나중에 혼자 보면서 다시 정리해볼 예정~
