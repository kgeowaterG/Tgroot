원하는 폴더에서 우선 
$git init 
명령으로 시작함.
그리고 처음 커밋을 하기 위해 다음 수행명령을 간단 수행한다. 
$echo "# P02" >> README.md
$git add README.md
$git commit -m "first commit"
$git branch -M main


-------------------------------------------
Git을 특정 폴더에 로컬로 만들고 특정 github 계정과 연결시키는 방식은 local user와 email을 만들고, (글로벌, 로컬 모두 가능함 글로벌은 ~ 디렉토리에 .)
git config --global user.name "My_name"    (영어이름 넣고) 
git config --globla user.email "My_email"  (이메일 주소 넣고)  --> ~/.gitconfig 에 기록됨

git config --local user.name "My_name"    (영어이름 넣고) 
git config --local user.email "My_email"  (이메일 주소 넣고)  --> mypathrepo/.git/config 에 기록됨
----------------------------------------------------------



일단 다음과 같은 내용을 참조하여 시작하면 된다. 다음 문자은 토큰을 사용하는 방법이며, 토큰은 다음과 같이 만든다. 
----
1. GitHub에서 토큰(PAT) 발급받기
.GitHub 로그인 후 우측 상단 프로필 클릭 → Settings 이동
.왼쪽 사이드바 맨 아래 Developer settings 클릭
.Personal access tokens → Tokens (classic) 선택
.Note: 'Fine-grained tokens'도 있지만, 처음이라면 설정이 간편한 'classic'을 추천합니다.
.Generate new token → Generate new token (classic) 클릭
.설정값 입력:
.Note: 토큰 이름 (예: My Laptop)
.Expiration: 만료 기간 (보통 30일~90일, 보안상 'No expiration'은 비권장)
.Select scopes: repo(전체), workflow, write:packages, delete:packages 정도를 체크합니다. (가장 중요한 것은 repo입니다.)
.맨 아래 Generate token 버튼 클릭

[!CAUTION]
토큰 생성 직후 나타나는 문자열을 반드시 따로 복사해 두세요. 창을 닫으면 다시는 확인할 수 없으며, 유출되면 타인이 내 저장소에 접근할 수 있으므로 비밀번호처럼 취급해야 합니다.

2. 터미널에서 토큰 사용하기 (Push 시 인증)
.이제 git push를 시도하면 인증 창이 뜰 때 토큰을 사용하면 됩니다.
.방법 A: 로그인 창이 뜨는 경우
  Username: GitHub 계정 아이디
  Password: **방금 복사한 PAT(토큰 문자열)**를 붙여넣기

.방법 B: URL에 토큰을 포함하여 등록 (이미 리모트가 연결된 경우)
  매번 입력하기 번거롭다면 원격 저장소 주소에 토큰을 미리 심어둘 수 있습니다.
-------------------
git remote add origin https://<토큰문자열>@github.com/<사용자명>/<저장소명>.git  (처음 origin 만들때)
git remote set-url origin https://<토큰문자열>@github.com/<사용자명>/<저장소명>.git (orgin의 리모트를 변경할 때)
-------------------



많이 쓰는 git 명령
$git --verison   (버전 확인)
$git remote -v  (리모트 지정 상황 확인)
$git log (그동안 커밋 등을 확인하기)
$git status (git의 상태를 점검한다)
$git checkout (기본적으로 브랜치 작업을 위한 일이며, HEAD가 pointing하는 사항 정의)
$git checkout -b [<newbranch>] (새로운 브랜치를 만듬 newbranch 라는 이름)
$git checkout branchname (brachname으로 Head 이동)