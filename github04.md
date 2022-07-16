```
git remote -v
git remote remove origin # origin 이 잘못 설정되어 있는 경우
git remote add origin https://github.com/alro923/test.git # alro923 부분을 본인 github id 로 설정

git remote remove upstream # remote 가 잘못 설정되어 있는 경우
git remote add upstream https://github.com/oss-team-A07/test.git

git fetch upstream main
git rebase upstream/main
git status
git diff
nano README.md
git add README.md
git rebase --continue
git push origin main -f
```
