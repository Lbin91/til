# Terminal command
**Bongjin Lee, iOS Dev**

터미널에서 자주 쓰이는 명령어

**ls**
list의 약자로 현재 디렉토리의 파일,폴더를 보여줌. 자주 쓰이는 옵션으로 -a가 있으며 숨겨진 파일도 보여준다
```
$ ls
```

**cd**
change directory의 약자로 폴더로 진입시 쓰인다. 뒤에 ..을 붙이면 현재 폴더를 나온다.
```
$ cd directory_name
```

**mkdir**
make directory의 약자로 현재 폴더에 새로운 폴더를 생성한다.
```
$ mkdir new_folder_name
```

**rmdir**
remove directory의 약자로 폴더를 삭제 한다. 단 폴더에 파일이 존재할 경우 이 방법으로는 지워지지 않는다.
```
$ rmdir delete_target_folder
```

**rm**
remove의 약자로 파일을 삭제한다. 폴더는 rmdir로 지운다. 단 -r 옵션을 사용시 폴더도 지워지며 **파일을 포함한 폴더**도 삭제 가능하다.
```
$ rm delete_target_file
$ rm -r delete_target_file
```

**cat**
concatenate의 약자로 파일의 내용을 출력한다.
```
$ cat file_name
```

**touch, echo**
파일을 생성한다. 단 echo는 파일의 내용까지 입력하면서 생성이 가능하다
```
$ touch file_name
$ echo "file_content" > file_name
```
echo의 경우 아래의 실제 결과를 보면 이해가 쉽다.

```
$ echo "test text" > text.txt
$ cat text.txt
test text
```

**history**
터미널에서 입력한 명령어 기록을 불러온다.
```
$ history
$ history 20 // 최근 20개의 명령어를 불러온다
!30 // 30번 명령어를 재 실행한다.
!! // 가장 최근 실행한 명령어를 재 실행한다.
!git // 최근 명령어 중 git 으로 시작하는 명령어를 재 실행한다.
```
