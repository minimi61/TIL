# 오늘의 일기

### git에 대해 알아보자
1. 깃(Git) : 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템. 소프트웨어 개발에서 소스 코드 관리에 주로 사용.
2. 깃허브 : 소프트웨어 소스코드 관리 서비스. 소스코드를 자유롭게 열람할 수 있고, 버그 관리, share 등 sns 기능도 있음.
3. Repository (저장소) : 로컬저장소, 원격저장소로 나뉜다.

* 로컬저장소 → 자신의 컴퓨터에 있음.
* 원격저장소→ 서버, 네트워크에 위치, 깃허브가 여기에 해당
* 기본적으로 로컬저장소에서 작업을 수행하고, 그 결과를 원격 저장소에 저장함.

#### shell 기초 명령어
- 홈디렉토리로 이동
$ cd ~ 

- 새 디렉토리에 디렉토리명 생성
$ mkdir [디렉토리명] 

- [디렉토리명]로 이동
$ cd [디렉토리명]

- 부모 디렉토리로 이동
$ cd ..

 - 현재 경로를 출력 // print working directory
$ pwd

 - 디렉토리 내용 출력
$ ls

 - 디렉토리의 폴더 상세 정보까지 출력
$ ls -l

 - 디렉토리의 숨김 파일과 디렉토리까지 출력
$ ls -a

 - 파일이 있는 디렉토리를 내용물과 함께 삭제 //remove
$ rm -r [디렉토리명]

 - vi 편집기로 [파일명. 확장자명] 파일을 작성
$ vim [파일명.확장명]

 +  현 위치에 파일 생성 //ex) touch a.txt
$ touch 

   + 문자열 출력 //ex) echo 'hello' > a.txt.파일에 hello 문자열삽입
    $ echo 

    + 확인용 명령어 //hello 문자열 확인 cat a.txt
    $ cat

    + 파일 복사 //cp a.txt hello/: hello라는 폴더로 a.txt가 복사됨
    $ cp


 - 터미널 창의 내용을 삭제
$ clear

 - 터미널 창을 종료
$exit



#### git 유저/업로드 설정(처음 git 다운받아 사용시)
 - 현재 위치에서 지역 저장소를 생성
$ git init

 - 깃환경에서 사용자 이름을  [사용자명]으로 지정
$ git config --global user.name "[사용자명]"

 - 깃환경에서 사용자 이메일을 [사용자이메일명]으로 지정
$ git config --global user.email "[사용자이메일]"

 - 깃의 상태 확인
$ git status

#### commit 명령어
 - git 메뉴얼
$ git --help

 - [파일명.확장자명]을 스테이지에 올림
$ git add [파일명.확장자명]

 + 커밋 메시지[메시지명]을 붙여 커밋
$ git commit -m "[메시지명]
    + -m은 message 의미, -c,-C,-F와 같이 쓸 수 없다
    + -C reuse-message
    + -c 사용자가 커밋메시지 추가로 편집 가능
    + -a 별도의 add 명령어 사용없이 수정된 파일에 대해 add, commit 한번에 수행(단, 한번도 add되지 않은 파일은 add를 따로 작업)
    + -am 은 a,m 옵션 합친 형태
    + -F 주어진 파일의 커밋 메시지를 가져온다

- 커밋 내역 확인
$ git log 

- 특정 커밋 내역 확인 
$ git show [커밋 id]

- 최근 버전과 작업 폴더의 수정 파일 사이의 차이를 출력
$ git diff
$ git diff [이전 커밋 id][이후 커밋 id]

- 지정한 커밋 해시로 이동
$ git checkout [커밋해시]

+ 가장 최근 커밋 취소
$ git reset 
    + $ git reset HEAD^ 현재 HEAD의 이전 커밋으로 되돌리기
    + $git reset HEAD~n 현재로부터 n번째 이전 커밋으로 되돌리기

+ 지정한 커밋 해시로 이동하고 커밋 취소
$ git reset [커밋 해시]
    + $ git reset --soft [커밋ID]  # head 만 바뀜
    + $ git reset --mixed [커밋ID] # staging 도 그 때로 바뀜
    + $ git reset --hard [커밋ID] # working디렉토리/staging 모두 그 때로 바꿈 



#### 브랜치 명령어
- 새로운 브랜치 [브랜치명] 생성
$ git branch [브랜치명]

- 브랜치 조회
$ git branch

- [브랜치명]으로 체크아웃(이동)
$ git checkout [브랜치명]<br/>
$ git checkout -b [브랜치명]  # 브랜치만들고 바로 이동

- 브랜치 삭제
$ git branch -d 브랜치명

- [브랜치명]을 master 브랜치와 병합 
$ git merge [브랜치명]

- merge 취소하기
$ git merge --abort

- merge 했다가 중간에 그만두고 싶을때
$ git reset --hard HEAD




#### git hub 원격저장소
- 원격 저장소에 연결
$ git remote add origin [github 레포지 주소]   
$ git remote add origin [branch 이름]   #없으면 생성됨

- 원격 저장소에 연결됐는지 확인
$ git remote -v

- 지역 저장소의 커밋을 맨 처음 원격 저장소에 올리는 경우
$ git push -u origin master (-u: --setupstream 서버의 main브랜치를 바라보게 하라는 명령어, 처음에만 쓰면 된다)


- 3번을 한 후에 지역 저장소의 커밋을 원격 저장소에 올리는 경우(업로드)
$ git push   
$ git push origin master

- 원격 저장소의 커밋을 지역 저장소로 가져옴
$ git pull   
$ git pull origin master

- SSH 키를 생성함
$ ssh-keygen   
> SSH(Secure Shell)는 원격지 호스트 컴퓨터에 접속하기 위해 사용되는 인터넷 프로토콜이다. 뜻 그대로 보안 셸
서버에 접속할때 비밀번호 대신 key를 제출하는 방식이다. 비밀번호보다 높은 수준의 보안요건을 필요로 할때 사용된다.


- 원격 저장소 복제하기(첫번째 커밋이 아니라면 pull 먼저하기)
$ git clone [원격 저장소 주소]

- 단순히 원격 저장소의 커밋만 확인하고 싶을 때(병합하지 않고)
* $ git fetch
    이후엔 diff로 비교
    * $ git diff test origin/test    브랜치 이름이 test일 경우 예시
    *  패치로 가져온 정보가 있는 브랜치\[FETCH\_HEAD\]로 이동   $ git checkout FETCH_HEAD

- [브랜치명]을 만드는 것과 동시에 체크아웃
$ git checkout -b [브랜치명] (-b는 new branch)

- 원격 저장소에 [브랜치명]의 브랜치의 커밋을 올린다
$ git push origin [브랜치명]

-원격저장소 삭제 $ git remote remove origin

#### 파일/보관 명령어(stash)

- 파일 내용 출력  
$ cat [파일명.확장자명]

- 디렉토리를 만드는 동시에 지역저장소 생성  
$ cd init [디렉토리명]

- 현재 커밋을 다른 브랜치에 있는 [커밋메시지] 커밋으로 되돌림  
$ git reset [커밋메시지] [커밋해시]

- 병합이 끝난 [브랜치명]을 삭제
$ git branch [브랜치명] -d (-d : delete)

- 마무리 하지 않은 작업 stash에 잠시 저장
$ git stash  
$ git stash save

- 보관한 내용을 목록을 출력
$ git stash list

- 보관한 내용을 적용  
$ git stash apply  
$ git stash apply stash@{1}

- 보관한 내용 중 가장 최근 항목을 삭제  
$ git stash drop  
$ git stash drop stash@{1}

- stash를 apply하고 제거(drop) 하기
$ git stash pop

#### 기타 명령어 
- 긴 명령어 짧게 이름 붙여 사용하기  
ex) git log --pretty=oneline을 ->git history 라는 별명으로 바꾸기.  
$ git config alias.[별명] '원하는 명령어'  
$ git config alias.history 'log --pretty=oneline'  

- tag 설정 하기  
$ git tag [태그이름][커밋 ID]  
$ git tag Version_2 86a99 # tag 달기  
$ git tag    #tag 조회하기  
$ git show Version_2  

> 출처 : https://gorokke.tistory.com/22

### 20220419
- 깃허브 커밋한 폴더, 파일명 변경하는 법
1. 변경하고 싶은 폴더가 있는 git 프로젝트 폴더로 이동
2. git mv 변경전폴더경로 변경하고자하는 경로   ($ git mv ./20220417.md ./About_git.md )   ( -mv는 Move or rename a file,)
3. $ git commit -m "커밋내용"
4. vscode 하단 변경된 부분 숫자를 누르고 커밋하면 끝!

- 잘못 올라간 폴더 및 파일 삭제하기
1. $ git rm --cached -r 폴더명   (cached가 없으면 로컬저장소 폴더 또는 파일도 삭제하므로 주의)
2. $ git commit -m "불필요한 폴더 및 파일 삭제"
3. $ git push -u origin main


### 20220524
- 컴퓨터로 작업해서 원격저장소에 올렸는데 노트북에 git pull해도 반영이 안된다
    -   해결방법: 
    -   배포/빌드 서버 등에 계속해서 최근 항목만을 가져오는 등의 경우나 로컬에 있는 모든 내용을 덮어쓰려는 경우 사용하면 될 것 같음(해당 브랜치 강제로 리셋)
    -   git fetch --all 
    -   git reset --hard origin/main

### 20220609
-    error: src refspec main does not match any 등장(git push 할 때)
-   git remote update -> git fetch 한 후 git status로 브랜치 확인 후 다시 해보기

### 20220616
-   로컬 저장소에 있는 프로젝트를 깃허브 사이트를 통해 만든 저장소로 push 하는 경우에 이런 메세지가 뜨는 경우가 있다.<br>
error: failed to push some refs to
-   git pull이 안될시에 git pull origin 브런치명 --allow-unrelated-histories 로 불러준다.
-   --allow-unrelated-histories   이 명령 옵션은 이미 존재하는 두 프로젝트의 기록(history)을 저장하는 드문 상황에 사용된다고 한다. 즉, git에서는 서로 관련 기록이 없는 이질적인 두 프로젝트를 병합할 때 기본적으로 거부하는데, 이것을 허용해 주는 것이다.

