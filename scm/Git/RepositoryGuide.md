## Repository 사용가이드

#### 프로젝트 신규 추가

- 선행작업으로 github.com 사이트 가입 후 진행합니다.
- 로컬 pc에 git을 설치합니다.

1. github.com 로그인시 우측상단의 <strong>' + '</strong>를 클릭후 New Repository를 선택한다.  

2. <strong>'Repository name'</strong> input박스에 사용할 프로젝트명을 입력하고 소스의 공개여부를 결정 후 <strong>'Create Repository'</strong> 버튼으로 생성을 완료한다.
(README파일, ignore설정, 라이센스 등 추가적인 기능은 필요시 찾아보도록 합시다~!)  

3. 버튼을 클릭시 화면이 전환되며 프로젝트가 생성이 되고 Code 탭에 command Line에서 설정하는 방법이 나옵니다.
    - cmd를 실행합니다.
    - 로컬에서 이미 작업한 프로젝트가 있다면 해당 폴더로 이동하고, 없는경우 폴더를 생성후 해당위치로 이동합니다.(파일이 없는경우 진행이 안될수도 있으니 폴더 생성 후 임시 파일README.md등을 만들어서 commit 하도록 합니다.)
    - github에서 repository생성시 샘플로 알려준 내용을 순서대로 실행합니다.


```
    git init
    git add *
    git commit -m "first commit"
    git branch -M main
    git remote add origin https://github.com/본인Repository경로
    git push -u origin main
```
4. github사이트에서 정상적으로 소스가 확인이 되면 프로젝트 추가 완료입니다.

#### 프로젝트(Repository) 삭제

- github 사이트에서 Repositories 탭으로 이동 후 삭제할 프로젝트를 선택합니다.  
Settings 탭으로 이동 > 스크롤 최하단으로 내리면 Danger Zone에서 Delete this repository를 선택 합니다.  
팝업이 뜨면 볼드체로 프로젝트 경로가 보일텐데 해당 경로를 input 박스에 입력 후 삭제 버튼을 클릭합니다.