# Init단계

repository 생성 https://github.com/dopplix/titan.git

Readme는 옵션

Git을 연동할 폴더에 파일을 넣은 후 우클릭 Git bash 실행(예 C:\git\Titan)

이거는 git bash를 킨 후 cd C:/git/Titan 한 것과 동일

\가 아니라 /임

git init 명령어 실행, 이 폴더에 깃을 사용하겠다는 의미

Initialized empty Git repository in C:/git/Titan/.git/ 가 뜨면 .git폴더가 생기면서 git을 사용할 준비가 됨

git add * 하면 commit 하기 전 공간에 반영이 됨

git status 하면 현재 add된 공간의 파일들과 현재폴더의 파일을 비교함

    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
    modified: bkexclient.cpp

git commit -m "메시지" 하면 local에 commit됨, -m은 message를 쓰겠다는 옵션

git log하면 현재 local의 commit된 내역을 볼 수 있음

    commit e99721f4e0168c77a35cc38ed23b3fe53f381504 (HEAD -> master)
    Author: msjeon <jmlambda@naver.com>
    Date: Thu Mar 26 08:51:33 2020 +0900

    bkex enter modified

    commit 6011e5bba4337615c256216308660c77c6c120b9
    Author: msjeon <jmlambda@naver.com>
    Date: Thu Mar 26 08:49:54 2020 +0900

    Titan First Commit

local에 git 커밋을 완료하면 

    git remote add org https://github.com/dopplix/titan.git

원래 org대신 origin을 사용하나 테스트 목적으로 org로 생성하였음

이 명령어를 실행하면 local에서 원격으로 push될 github의 주소를 local의 org 변수에 등록한 것

    git remote -v 
    
로 org에 https://github.com/dopplix/titan.git가 들어간 것을 확인 가능

    git push org master

이 상태에서는 (master)가 현재의 branch임 따라서 org이라는 주소에 현재 local의 master branch를 push함

github에서 파일을 확인

# 수정단계

git폴더에서 작업을 완료함

git에 push하려면 작업폴더에서 우클릭 - git bash

git status를 확인하면 변동내역을 확인 반영되지 않은 수정내역은 적색으로 표시

git add *로 commit을 준비함

git status를 확인하면 commit 할 파일은 녹색으로 표시

git commit -m "Message" 하면 local에 commit됨

    git log

```git
commit 7aace42c46c5db525d7d96b6b972b8d37a94b2b1 (HEAD -> master)
Author: msjeon <jmlambda@naver.com>
Date: Thu Mar 26 09:11:51 2020 +0900

Git First Modify Test

commit e99721f4e0168c77a35cc38ed23b3fe53f381504 (org/master)
Author: msjeon <jmlambda@naver.com>
Date: Thu Mar 26 08:51:33 2020 +0900

bkex enter modified

commit 6011e5bba4337615c256216308660c77c6c120b9
Author: msjeon <jmlambda@naver.com>
Date: Thu Mar 26 08:49:54 2020 +0900

Titan First Commit
```

HEAD는 현재 local이 바라보고 있는 branch

org/master는 현재 remote가 바라보고 있는 commit임

git push org master하면 github에 push됨

# 확인단계

github에서 해당 commit을 확인하면

이전 commit과의 차이를 명확히 볼 수 있음

# GitIgnore

최상위 폴더(.git이 있는 폴더)에 .gitignore 파일을 생성

출처 : https://gmlwjd9405.github.io/2017/10/06/make-gitignore-file.html

>.gitignore 이란?
.gitignore 파일이란 Git 버전 관리에서 제외할 파일 목록을 지정하는 파일 이다.
git으로 프로젝트를 관리할 때, 그 프로젝트 안의 특정파일들은 관리할 필요가 없는 경우가 있다. 예를 들면, 프로젝트 설정파일, 자동으로 생성되는 로그파일(ex.*.log), 빌드할 때 생기는 컴파일된 파일(ex. *.class) 등이 있다. 따라서 이런 관리할 필요가 없는 파일들을 git이 track 하지 않도록 .gitignore을 설정하는 것이다.

.gitignore 파일에 내용 채우기

GitHub에서 거의 모든 언어에 대한 .gitignore 파일을 미리 만들어서 제공하고 있다. github/gitignore를 참고하여 .gitignore 안의 내용을 채우면 된다.

개인이 직접 .gitignore 파일을 설정하고 싶으면 git-scm.com/docs/gitignore 를 참고하여 .gitignore 안의 내용을 채우면 된다.

## a comment - 주석이므로 이 줄은 무시한다.

- 확장자가 .a인 파일 무시

```
*.a
```

- 확장자가 .a인 파일은 무시하도록 했지만 lib.a는 무시하지 않는다.

```
!lib.a
```

- build 디렉토리에 있는 모든 파일은 무시한다.

```
build/
```

- .o나 .a인 파일은 무시한다.
```
.[oa]
```

출처: https://glshlee.tistory.com/41 [Hello World!!]

- 참고

git rm -r --cached . 하면 local의 모든 cache를 삭제하는 것

local 에 있는 모든 cache들을 삭제한 후 새로 commit하면 ignore된 파일은 앞으로 commit되지 않고 remote repository에서는 삭제됨

cache에는 tracking하고있는 파일들이 기록되어 있음

rm은 remove, -r은 recursive를 의미, recursive가 필요한 이유는 폴더가 존재 시 폴더 내부로 진입하여 전부 삭제하기 위함

cache 삭제 후 다시 add, commit, push를 거치면 remote repository에서 gitignore 이전 commit되었던 파일들이 삭제됨

git add할때는 해당 폴더의 excel 등 pemmision에러나는 파일들을 종료한 후 add할 것

# 계정 설정 및 확인

```git
git config --global user.email "jmlambda@naver.com"
git config --global user.name "msjeon"
git config user.email
git config user.name
```
출처:
https://help.github.com/en/github/using-git/setting-your-username-in-git


# Clone

```git
cd c:
cd git
git clone https://github.com/dopplix/react-youtube-learner.git
```

# Pull
- 최종 커밋 상태로 되돌림
```git
git reset --hard
```

- github에서 가져오기

```git
git remote -v 
git pull org master
```

# Tips

    ls

현재 폴더의 하위 폴더를 나열

    cd ..

상위 폴더로 이동

앞자를 쓴 후 tab을 누르면 자동완성, 한번 더 누르면 선택할 수 있는 하위 폴더 리스트 나열

# Reset Revert

http://www.devpools.kr/2017/01/31/%EA%B0%9C%EB%B0%9C%EB%B0%94%EB%B3%B4%EB%93%A4-1%ED%99%94-git-back-to-the-future/

# 특정 커밋으로 이동

    git checkout <hash>

# fetch와 pull의 차이

pull은 코드만 가져오고 fetch는 branch들을 가져옴
