# git
1. 배운점
   오늘은 git에 대해 배웠다.
   git : 분산 버전 관리 시스템
   버전의 변화만 기록하고 추적한다 (전체 파일 다 저장하면 용량 낭비)

# git의 3가지 영역
 
### Woking Directory
실제 작업 중인 파일들이 있는 곳

### Staging Area
중간 준비 영역 같은곳 이다.
커밋을 하기 위해선 SA를 거쳐 가며, 눈으로 볼 수 는 없지만 명령어로 볼 수 있다.
git add **파일명**

### Repository
 버전이 쌓이는 영역이다. 커밋을 하면 여기에 모인다.
 like a snapshot = commit (stage에 있는걸 사진찍은것이 커밋에 모인다.)
 git commit -m **"파일명"**


**git init** - 로컬 저장소 설정 (initialization의 약자로 초기화)
바탕화면에서 하면 하위 전부다 로컬 저장소 설정이 되어, 추가로 만들기 어렵게 영역이 제한된다.
그래서 특정 폴더를 만들고 그 영역에 대해 설정을 해야 한다.
**프로젝트 시작할때 처음에 하고 시작해야한다**
clone으로 가져오는 경우에는 하지 않는다.

**git add** 
WD -> SA로 옮기기.

**git commit**
SA -> Repo
git commit -m "이름"
-m : message (이름저장)

**git status**
깃의 상태보기
빨간색 - Working Directory
초록색 - Staging Area

처음커밋은 초록색 빨간색 문구가 new로 나오지만, 두 번째 부터는 modified로 나온다.

**git log**
커밋한 Repository를 확인한다.
git log --oneline : commit 목록 한줄로 보기

## git 주의사항 ##
1.  git 저장소 내부에 git 저장소는 위치 할 수 없다.
2.  git init을 하는 순간 어떤 숨김폴더가 생성된다. git 자체를 지울려면 숨김파일보기해서 파일 자체를 지우면 된다.

**git config --global -l**
git global 설정 보기 (나의 깃허브 아이디랑 이름 보기)

깃은 노란색 코드로 구분한다. 파일명은 사람을 위한 것

**vim 에디더**
1. 수정모드 (내용을 작성하는 모드)
2. 명령모드 (저장.삭제,나가기...)

명령 -> 수정모드 : i
수정 -> 명령모드 : esc
쓰기 : w
나가기 q

git 메시지를 바꾸면 = 커밋 자체를 새로운 커밋으로 바꾼다.

**git commit --amend**
staging Area에 있는 빼먹은 커밋 같이 커밋하는 걸로 바꾸기

# 깃허브

**원격 저장소**
코드와 버전 관리 이력을 온라인에 올리겠다.
협력, 백업을 위해

local -> github
remote 등록이 필요하다.

**git remote add [origin] [remote] [_repo_url]**
매번 원격저장소에 나의 레포 url 입력하는게 번거로우니까
별칭을 등록한다. orgin이 별칭. 보통 많이 쓴다.

**git remote -v**
원격 저장소에 나의 별칭이 잘 연결되었는지 확인한다.

## 파일 올리기

**git push origin master**
origin 원격저장소에 master에 있는 것을 커밋하겠다. 라는 의미
***한 번 인증 받으면 컴퓨터에서 계속 사용이 가능하며, windows 자격증명에 들어가 인증서 삭제도 가능하다***
원격 저장소는 commit된 내용만 올라간다. (커밋을 하지 않았다면 push는 불가능하다.)

**pull or colone**
내려받는 것은 똑같은데,
clone은 전체 다운로드 
pull은 변경사항 만큼만 다운로드 한다. (업데이트)

**git pull origin master**
**git clone remote_repo_url**
clone으로 가져오는경우 url을 입력해야 한다.
git init은 안해도 된다.(이미 되어 있음)
clone은 처음에 전체복사 느낌이고
pull은 업데이트 사항만 비교해서 가져오는 느낌이다.

Github에서 Repository 만들 때
READEME.md 체크하고 만들면, push가 되지 않는다. 
올바른 시작은 clone 부터 시작해야 한다.

### gitignore
사용자 정보, 패스워드, 암호화 키 같은것은 원격 저장소에 올리면 안된다.
따라서 애초에 처음부터 로컬 commit에 포함이 되지 않게 한다.

.gitignore 파일을 생성하여, 해당하는 파일명을 작성한다.
맨 처음에 개발 시작할때 넣어놓고 시작해야 한다 (한번 이라도 깃의 추적이 시작되면 나중에 넣으면 안된다.)
gitignore.io 들어가서 운영체제,언어,개발환경 별 무시하는 코드 정리되어있다. 

git rm --cached(비상시 명령어)

## 깃허브의 목적

1. 협업 목적
2. 포트폴리오 목적 
   
TIL (today i learned)
앞으로 배운것과
문제를 해결하는 과정을 정리해보자