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


※ 접근이 안 되서 netstat -anp | grep 3306으로 확인 해 보니 tcp가 아니라 tcp6… tcp6는 IPv6란 거. <br>
변경하는 법은 /etc/my.cnf.d/server.cnf 안의 bind-address=0.0.0.0 의 주석을 풀고,  서버 재기동 <br>
--> 이 때의 mariaDB 버전은 10.1 <br>




1. 운영체제 확인<br>
  - OS의 버전을 확인한다. cat /etc/*release* <br>


2. repository 설정<br>
 ※ Repository를 삭제하기 원할 경우. 설정 파일만 삭제하면 된다. rm -f /etc/yum.repos.d/MariaDB.repo <br>
   - [Ruby](http://mariadb.org/) 웹페이지 방문<br>
   - 패키지 다운로드가 아닌, yum repository 정보 페이지로 이동. <br>
     Download(a) > repository(b) > 이후 운영체제, OS버젼, 설치하기 원하는 버전 선택(c) 시 하단에 repository  설정 내용이 보여진다<br>
     ![download](https://user-images.githubusercontent.com/39476251/112238473-14f56700-8c88-11eb-9694-77218b47acf1.JPG)
     ![download2](https://user-images.githubusercontent.com/39476251/112238562-3bb39d80-8c88-11eb-99d3-1ec5b025ac84.JPG)
   - yum repository 설정 파일 위치 <br>
     : /etc/yum.repos.d  하위에   repo라는 확장자로 파일들이 존재 <br>
   - 기존 파일에 추가해도 무방하나, 관리의 용이성을 위해, 신규로 파일 생성(MariaDB.repo) <br>
   - 2번항의 내용을 그대로 작성하여 저장. <br>
   - yum repolist 명령어를 이용하여 repository 정보를 제대로 읽어오는지 확인 <br>
     ![download3](https://user-images.githubusercontent.com/39476251/112238666-73224a00-8c88-11eb-86a7-7a8a8afb276f.JPG)


3. yum을 이용한 install<br>
   - yum install MariaDB-server 명령어를 입력한다. <br>
     이 때 client도 설치하고 싶을 경우, 뒤에 MariaDB-client 만 붙여주면 된다. ex) yum install MariaDB-server MariaDB-client <br>
   - 중간에 확인창에서는 y 입력. <br>
   - 설치 완료 후 설치 확인. rpm -qa | grep MariaDB <br>
     ![download4](https://user-images.githubusercontent.com/39476251/112238775-a4027f00-8c88-11eb-80a0-cefa493c740c.JPG)
     
     
4. DB 시작 및 정지<br>
   - DB 시작<br>
     a. cd/etc/init.d<br>
     b. ./mysql start<br> 
     또는 a. /etc/init.d/mysql start<br>
   - DB 정지<br>
     a. cd/etc/init.d<br>
     b. ./mysql stop<br>
     또는 a. /etc/init.d/mysql stop<br>
 ※ systemctl start mariadb.service<br>
    systemctl stop mariadb.service<br>
    mts 에서 사용하기 위해 라즈베리에 설치한 결과, mysql 시작 정지로 불가. ( 폴더에 mysql 실행 파일이 없음 )  <br>
    systemctl start mysql.service => 불가  <br>
    ==> 그런데. ps -ef | grep mysql 하면 또 나오네? 아놔… 얘네 뭐야..<br> 
     

5. 관리자 계정 비밀번호 설정<br>
   - 관리자 비밀번호가 설정되어 있지 않으므로, 설정 해 준다. <br>
     /usr/bin/mysqladmin -u root password 'qweasd' 또는 <br>
    cd /usr/bin <br>
    ./mysqladmin -u root password 'qweasd' <br>
    패스워드는 ' 으로 감싸준다. <br>
    
    
6. 관리자 계정 접속<br>
   - mysql -uroot -p 이후 비번 입력<br>


7. DB 생성<br>
   - 데이터베이스 조회 show databases;
   - 데이터베이스 생성 create database DB명; <br>
     => 이 때 캐릭터셋을 명시하여 생성해 주는 것이 좋음 create database DB명 character set utf8;<br>


8. USER 생성<br>
   - 기본 DB로 이동 (계정 정보등이 저장되어있는 기본 DB가 존재) use mysql;<br>
   - 계정 정보 확인 select host, user from user; <br>
   - 계정 생성 create user '아이디'@'%' identified by '비밀번호'<br>
   - local에서 접속하고 싶다면, 계정을 따로 생성해줘야 한다.<br>
     create user '아이디'@'localhost' identified by '비밀번호'<br>


9. 권한 부여<br>
   - user에게 권한 부여. grant all privileges on DB명.테이블명 to USER명; <br>
   ※ all privileges : 모든 권한 부여 <br>
      select, insert : select, insert 권한만 부여 <br>
      등등 원하는 권한만 ','를 이용하여 구분 <br>
   ※ DB명.Table명 : 해당 DB의 특정 Table에만 해당 권한 부여 <br>
      Db명.* : 해당 DB의 모든 Table에 해당 권한 부여 <br>
      *.* : 모든 DB의 Table에 대한 해당 권한 부여 <br>
      DB명에 %로 특정 DB들에 대한 설정도 가능하다.<br>
      ex) DB_1, DB_2, DT1이 있다고 가정했을 때, DB_%.* 로 설정할 경우, DB_1과 DB_2  DB에 대한 모든 Table에 해당 권한을 부여한다. <br>


10. 권한 적용<br>
   - mysql 접속 상태에서 flush privileges; 또는 서버 재기동<br>


11. 캐릭터셋 설정<br>
   - [Ruby](http://roqkffhwk.tistory.com/133<br>
   - [Ruby](https://www.lesstif.com/pages/viewpage.action?pageId=20775198 )<br>
   - [Ruby](https://slobell.com/blogs/38)<br>
   - [Ruby](https://www.lesstif.com/pages/viewpage.action?pageId=20775198 )<br>
   - [Ruby](https://www.enteroa.com/2016/01/26/database-create-%EB%AC%B8%EC%97%90%EC%84%9C-%EC%BA%90%EB%A6%AD%ED%84%B0%EC%85%8B-%EC%A7%80%EC%A0%95%ED%95%98%EC%97%AC-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0/) : DB생성 시 캐릭터셋<br>
