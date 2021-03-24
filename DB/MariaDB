# 설치

1. 운영체제 확인
2. repository 설정
3. yum을 이용한 install
4. DB 시작
5. 관리자 계정 비밀번호 설정
6. 관리자 계정 접속
7. DB 생성
8. USER 생성
9. 생성한 USER에게 권한 부여
10. 권한 적용
11. 캐릭터셋 설정

※ 접근이 안 되서 netstat -anp | grep 3306으로 확인 해 보니 
tcp가 아니라 tcp6… tcp6는 IPv6란 거. 
변경하는 법은 /etc/my.cnf.d/server.cnf 안의 bind-address=0.0.0.0 의 주석을 풀고,  서버 재기동 
--> 이 때의 mariaDB 버전은 10.1 


1. 운영체제 확인
- OS의 버전을 확인한다. cat /etc/*release* 

2. repository 설정
 ※ Repository를 삭제하기 원할 경우. 설정 파일만 삭제하면 된다. rm -f /etc/yum.repos.d/MariaDB.repo 
 - [Ruby](http://mariadb.org/) 웹페이지 방문
 - 패키지 다운로드가 아닌, yum repository 정보 페이지로 이동. 
   Download(a) > repository(b) > 이후 운영체제, OS버젼, 설치하기 원하는 버전 선택(c) 시 하단에 repository  설정 내용이 보여진다
   ![download](https://user-images.githubusercontent.com/39476251/112238473-14f56700-8c88-11eb-9694-77218b47acf1.JPG)
   ![download2](https://user-images.githubusercontent.com/39476251/112238562-3bb39d80-8c88-11eb-99d3-1ec5b025ac84.JPG)
 - yum repository 설정 파일 위치 
   : /etc/yum.repos.d  하위에   repo라는 확장자로 파일들이 존재 
 - 기존 파일에 추가해도 무방하나, 관리의 용이성을 위해, 신규로 파일 생성(MariaDB.repo) 
 - 2번항의 내용을 그대로 작성하여 저장. 
 - yum repolist 명령어를 이용하여 repository 정보를 제대로 읽어오는지 확인 
   ![download3](https://user-images.githubusercontent.com/39476251/112238666-73224a00-8c88-11eb-86a7-7a8a8afb276f.JPG)

3. yum을 이용한 install
 - yum install MariaDB-server 명령어를 입력한다. 
   이 때 client도 설치하고 싶을 경우, 뒤에 MariaDB-client 만 붙여주면 된다. ex) yum install MariaDB-server MariaDB-client 
 - 중간에 확인창에서는 y 입력. 
 - 설치 완료 후 설치 확인. rpm -qa | grep MariaDB 
   ![download4](https://user-images.githubusercontent.com/39476251/112238775-a4027f00-8c88-11eb-80a0-cefa493c740c.JPG)
