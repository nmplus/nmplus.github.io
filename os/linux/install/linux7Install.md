# CentOS 7 - 설치

0. 설치준비  

centos 설치하기 위해 먼저 ISO파일을 다운로드를 받는다.  
https://www.centos.org/centos-linux/  

일반 pc나 노트북이라면 x86_64 선택 후 mirror사이트중 카이스트, 네이버, 카카오 이런데서 다운 받는다.(속도가 잘나옴..)  

CentOS-7-x86_64-DVD-2009.iso 파일이 full버전이며 다운받아서  

rufus툴등을 이용해서 설치usb파일을 만든다.  

1. usb 부팅  

Install CentOS 7 선택 

2. 언어및 키보드 선택  

한국어 선택  

3. 설치 대시보드  

  3-1. 날짜 & 시간, 키보드, 언어 지원은 기본값으로 설정되어 있음.  

  3-2. 소프트웨어 영역에서 소프트웨어 선택 클릭시 OS 설치시 어떻게 선택할것인지 나온다.  
       보통 Minimal OS로 설치를 하며 GUI를 사용 할 경우 해당하는 부분을 선택 후 진행하면 된다.
  
  3-3. 시스템은 파티션과 네트워크 연결부분을 선택한다. 네트워크는 랜선으로 연결시, 무선연결시 해당하는 상황에 맞게 선택하면 된다. 파티션 설정은 만약 현재 파티션이 지정된 경우 초기화를 진행 후 파티션을 설정한다. 수동으로 파티션을 구성하는 경우에는 파티션 타입을 선택하여 마운트 경로 용량 등을 구성한다.

```
수동 파티션 설정
/ - 리눅스 시스템의 최상이 디렉토리  
/root - 시스템 관리자의 홈 디렉토리  
/boot - 부트 디렉토리, 리눅스 부팅을 관리하는 디렉토리  
/var - 동적파일 디렉토리  
       시스템 로그파일, 유저로그인 보안 기록 등 정보저장
/home - 사용자 계정을 위한 디렉토리
/tmp - 임시 디렉토리
/usr/local - 프로그램 관리 디렉토리
swap - 리눅스 메모리 보조용으로 용량 설정
```

4. 설치시작버튼 클릭

root의 암호를 설정하며 설치가 진행되며 완료시 재부팅버튼 선택한다.
(사용자를 생성한다.)

5. 재부팅

라이센스 등록, 사용자를 생성하지 않았다면 현재 step에서 추가 할 수 있다.
네트워크를 선택 하지 않은 경우 네트워크를 연결한다.
설정한계정으로 로그인 후 터미널에서 yum update를 수행한다.(root권한에서..) 끝.
(OS 정보 cat /etc/\*release\*)


