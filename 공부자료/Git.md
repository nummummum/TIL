# Git Basic - Interface

## 기본 인터페이스

> **git init** : Git의 사용(시작)을 알려주는 명령어. 현재 디렉토리에 Git의 저장소를 초기화 시킨다. .git이라는 디렉토리가 생기는데 버전정보를 담고있다.

git 명령어 뒤에 —help 를 주면 그 명령어의 상세 옵션을 알려준다.

> **git status** : 현재 디렉토리의 상태를 보여준다. 추가, 수정, 삭제 된 파일은 추적되지않고 무시하므로 변경을 원할 시 add 를 통하여 파일을 추가해줘야한다.

> **git add 파일이름** : 파일을 추가해준다. 프로젝트를 진행 시 임시로 필요한 파일들은 버전 관리를 하면 안 되기 때문에 add를 통하여 파일을 추가해 git이 변경된 파일을 찾아가게 한다. add를 하면 저장소(repository)에 commit을 하기위한 대기상태(stage)가 된다.

> **git config —global user.name 이름, git config —global user.email 이메일** : 버전들이 누가 만들었는지 알려주기 위하여 기본 정보를 세팅하는 명령어. 한 번 만 해주면 된다.

> **git commit** : Git의 버전을 생성한다.

- -a : 수정한 삭제한 파일은 자동으로 추가를 하여 add 과정을 스킵을 해도 된다. 한 번도 add 안 했을 시에 작동 안 하므로 적어도 1번의 버전관리(add)가 필요하다.

- -m : 메시지를 명령어에서 작성한다.

(ex : git commit -am “Message”) add 과정과 commit 메시지 입력을 동시에 해준다.

> **git log** : Git의 로그를 확인 할 수 있다. (commit 날짜, 이름, 이메일 등)

- -p : commit한 소스 사이에 차이점을 알 수 있게 해준다.

- commit의 ID : commit ID 이전의 메시지만 볼 수 있다.

- —branches —decorate —graph : branch 로그들의 최신 commit들을 표시하여 보여준다. graph 효과를 주어 작업을 가지형식으로 파악 할 수 있게해준다.

- (branchID 1)..(branchID 2) : branchID 1에는 없고 branchID 2에는 있는 로그를 알려준다.

> **git diff (commitID 1)..(commitID 2)** : 두 commit의 차이점을 알 수 있다. add를 사용하기 전에 git diff를 사용하면 commit하기 전 문제가 있는지 없는지 확인 할 수 있는 기회를 제공한다. add를 한 후에 diff 사용하면 코드가 보이지 않는다. commitID 대신 branchID도 넣을 수 있다.

> **git reset (commitID 1) —hard** : commitID 1 부분을 최신 버전의 상태로 되돌리고 그 이후에 버전은 삭제된다. 하지만 실제로는 버린게 아니라 남아있다. (눈에 보이지는 않는다.) **협업 시 저장소의 버전들을 올릴 때 공유 후 reset은 절대 하면 안 된다.** reset하는 commit은 공유 전에 내 컴퓨터에만 있는 버전을 대상으로 해야한다.

> **git revert (commitID 1)** : reset과 비슷하지만 최신 버전의 상태를 새로 만든다.

> **git branch 브랜치이름** : Branch를 만든다.

-d : branch를 삭제한다.

> **git checkout 브랜치이름**: Branch를 바꾼다.

-b : 브랜치를 만들고 checkout를 하는걸 한번에 할 수 있다.

> **git merge 브랜치(끌고올)**: 현재 Branch에 끌고올 Branch를 넣는다

> **git stash**: Working Directory의 변경사항을 감춘다.

- -list : stash된 리스트를 확인한다.

- -apply : 최신 statsh가 적용된다.

- -drop : 최신 stash를 삭제한다.

- -pop : 최신 stash가 apply되고 drop이 된다.(두 기능을 합친 것)
