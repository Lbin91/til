<<<<<<< Updated upstream
# 유용한 git command 모음
## Bongjin lee, iOS developer

개발 경력 3년에 이르렀지만 유독 terminal 레벨의 CLI 방식으로의 git 관리는 익숙해 지지않아 sourcetree, fork 등의 GUI 클라이언트를 이용해 개발을 지속해왔습니다.
그마저도 전 직장에서는 별도의 branch 생성도 없이 main branch에 commit 하는 행동만 했을 뿐 제대로 활용하지 못했었습니다.
다행히 현 직장에서는 목적을 위한 branch 분리 및 rebase를 활용해 깔끔한 commit history 정리 등의 더 많은 활용을 진행하였습니다.

이번 TIL을 git을 통해 작업하면서 git의 CLI 명령어와 활용방법을 정리해보며 실제로 손에 익을 때 까지 형상관리를 CLI로 진행할 계획입니다.
=======
#git command 정리
Bongjin Lee, iOS Dev

타겟 폴더에 git 작업을 시작하기 위해 git 설치
```
$ git init
```
위 명령어를 실행하면 폴더에 .git이 생성되며 숨겨진 상태라 보이지는 않음

GitHub등의 외부 저장소에서 git을 연결하기 위해서는 
* clone {github.repository.url}
* remote add origin {github.repository.url} 후 pull

대충 이정도 2가지가 가능함.

지금부터는 간편하게 쓰기 위해 최소한의 설명과 명령어를 나열함.
***
```
remote로 코드를 받아와 저장소에 저장한다
$ git pull

remote에서 데이터 받아와 갱신(코드가 바뀌진 않음.)
$ git fetch

브런치 생성
$ git branch -m branch_name
(만일 브런치 생성 시 git not a valid object name 'master' 이런 오류가 발생한다면 커밋이 하나도 없는데 branch 생성해서 발생한 오류임)

커밋 할 파일을 추가
$ git add file_name

변경되어 있는 모든 파일을 커밋에 추가
$ git add .

변경되어 있는 파일 등의 리스트를 보려면
$ git status

추가된 파일을 commit 하기
$ git commit -m "commit_message"

remote branch에 push 하는 법
$ git push remote_repo_name branch
(보통의 경우
$ git push origin develop
같은 느낌)

로컬 브랜치 보기
$ git branch -a

원격 브랜치 보기
$ git branch -r

브랜치 이름 변경
$ git branch -m old_branch_name new_branch_name

로컬 브랜치 삭제
$ git branch -d branch_name

원격 브랜치 삭제
$ git push remote_repo --delete branch_name

커밋 안한 변경사항 임시저장(stash)
$ git stash
$ git stath save "stash_memo"

최근 stash 불러오기
$ git stash pop

커밋 히스토리 조사(q 누르면 나가짐)
$ git log

커밋의 디테일한 히스토리
$ git log --stat

최근 커밋 2개의 차이점 보여주기
$ git log -p -2
```

## reset과 revert 차이
reset과 revert 둘다 commit을 되돌리는 기능이지만 차이점이 존재한다.
**reset**
reset의 경우 아예 없던일이 되어버려서
a -> b -> c -> d 로 commit이 쌓인 상태에서
d에서 b로 reset을 한다면
1. ```$ git reset --hard b_commit_id```의 경우 b 커밋으로 돌아가고 c,d에 해당하는 작업 자체가 삭제됨
2. ```$ git reset --mixed b_commit_id```의 경우 b 커밋으로 되돌아가고 c,d에 해당하는 작업 내용은 남아있는 상태(stage 안된상태 즉 add 되지 않음)
3. ```$ git reset --soft b_commit_id```의 경우 b 커밋으로 되돌아가고 c,d에 해당하는 작업 내용은 남아있는 상태(stage 된 상태, 즉 commit 하기 직전)

**revert**
동일한 상황에서 d에서 b로 revert 한다면
```$ git revert d_commit_id```
```$ git revert c_commit_id```
순서로 진행되어야 하고 커밋 히스토리에는
a -> b -> c -> d -> **d'** -> **c'** 가 되어 b commit 상태로 되돌아 가게 됨.
즉 revert는 데이터 결과는 reset hard와 동일하지만 commit 히스토리에 기록이 된다는 차이점이 존재함.

## **일단은 끝!**
>>>>>>> Stashed changes
