
# Git

### 먼저 할 일
[GitHub 가입](https://github.com/)  
[Git 설치](https://git-scm.com/download/)  

**깃 cmd창에서 이용**

### 최초설정
깃 설치 후 사용자 정보 등록 필요  
```
git config --global user.name "{사용자이름}"
git config --global user.email {이메일주소}
```
깃 설정정보 조회  
git config --list

깃 저장소로 사용할 곳에서 git init 으로 저장소 생성

계정 정보 삭제  
git config --unset --global user.name  
git config --unset --global user.email  

자격 증명 관리자 -> Windows 자격 증명 -> git 관련 제거

### Repository 초대 방법
1. GitHub에서 초대할 Repository로 이동
2. Settings -> Collaborators -> Add people -> 초대할 사람 Username 입력 후 선택 -> Select a collaborator above

### Repository 초대 받은 경우
1. GitHub 계정 메일 접속
2. 메일에서 View Invitation 클릭
2. 이동한 GitHub 페이지에서 Accept invitation 버튼 클릭
3. git clone {원격저장소주소}

### Repository Clone 원격 저장소 복제
1. 깃허브 페이지에서 복제할 원격 저장소 URL 확인
2. cmd 창에서 진행  
git clone {원격저장소주소}

혹시 이런 에러 뜨며 진행 되지 않는 경우
```
fatal: remote error:
    /{사용자이름}/{원격저장소} is not a valid repository name
    Visit https://supprot.github.com/ for help
```
해결방법  
git clone https://{깃허브아이디}:{토큰}@github.com/{원격저장소주인아이디}/{원격저장소명}.git  
예시)  
kim1207 / eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9 (깃 정보)  
hong0510 / springBoot (원격저장소 정보)  
git clone https://kim1207:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9@github.com/hong0510/springBoot.git

#### GitHub Token 생성 방법
깃허브 계정 -> Settings -> Developer settings -> Personal access tokens -> Generate new token  
Note : 토큰 이름  
Select scopes : 허가할 권한 체크  
-> Generate token  
**토큰은 생성했을 때 1번만 보여준다.  
토큰 등록하면 다시 확인할 수 없으므로 잊어버리면 삭제 후 재생성**

### 명령어
- git init  
현재 디렉토리를 깃 저장소로 생성
- git status  
파일 상태 확인
- git add fileName  
해당 파일을 Staging Area로 이동
- git commit -m "message"  
Staging Area에 있는 파일을 로컬저장소로 커밋
- git push  
로컬저장소 커밋 원격저장소로 올리기
- git pull  
로컬저장소로 원격저장소 커밋 가져오기
- git log  
커밋 로그 확인
- git branch  
브랜치 목록 조회
현재 사용중인 브랜치 앞에는 * 붙음
- git branch {브랜치이름}  
브랜치 생성  
**기본 브랜치 master 아닌 main 이용하기**
- git checkout {브랜치이름}  
브랜치 이동 
- git merge {브랜치이름}  
브랜치 병합
- git branch -d {브랜치이름}  
브랜치 삭제

### SVN과의 차이점
SVN은 commit 하면 바로 저장소에 반영되지만  
**Git은 commit 후 push 까지 해줘야 원격저장소에 반영된다.**

![깃영역](https://user-images.githubusercontent.com/39661858/167563800-fe1f285e-ce53-4e3f-800e-223e31d571f0.png) 

### Git 영역
- Working Directory : 내가 작업하고 있는 곳
- Staging Area : git add 명령어로 커밋하기 위한 파일들이 있는 곳
- Repository (git directory) : 커밋한 파일들이 모여있는 저장소
