### ❣Github 사용법
<br>

💜 공통

```bash
git config --global user.name "[user name]"
git config --global user.email "[user email]"
```

- [x] email 오타나면 잔디 안심어지니 유의하자!!!

```bash
git pull origin main	//push하기전에 반드시 pull 먼저 해주기!

git add .
git commit -m "[commit message]"
git push origin main
```
<br>


💜 폴더 자동 생성 (clone)

- github에서 repository 생성

```bash
git clone [repository url]
```
<br>


💜 생성되어있는 폴더에 연결

- readme 파일 우선 생성하지 말고 진행

```bash
git init
git remote add origin ["repository url"]
git branch -M main
git push -u origin main
```
<br>


💜 git igonre파일 생성

- 참조사이트 : https://www.toptal.com/developers/gitignore

- 작성법 (.gitignore)

```bash
# 특정 파일 무시
파일명.확장자

# 해당 확장자 파일 전체 무시
*.확장자

# 해당 폴더안의 파일 전부 무시
폴더명/

# 해당 폴더안의 해당 확장자 파일 전부 무시
폴더명/*.확장자

# 해당 폴더 포함 하위 모든 폴더의 해당 확장자 파일 전부 무시
폴더명/**/*.확장자

# 햔제 폴더의 해당 확장자 파일 전부 무시
/*.확장자
```

- git CMD에서 기존 commit 기록 삭제

```bash
git rm -r --cached .
git add .
git commit -m "Apply .gitignore"
git push origin main
```
