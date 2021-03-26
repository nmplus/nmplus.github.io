# MARIA DB

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
   - [http://mariadb.org/](http://mariadb.org/) 웹페이지 방문<br>
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
    - [http://roqkffhwk.tistory.com/133](http://roqkffhwk.tistory.com/133)<br>
    - [https://www.lesstif.com/pages/viewpage.action?pageId=20775198](https://www.lesstif.com/pages/viewpage.action?pageId=20775198)<br>
    - [https://slobell.com/blogs/38](https://slobell.com/blogs/38)<br>
    - [https://www.lesstif.com/pages/viewpage.action?pageId=20775198](https://www.lesstif.com/pages/viewpage.action?pageId=20775198)<br>
    - [https://www.enteroa.com/2016/01/26/database-create-%EB%AC%B8%EC%97%90%EC%84%9C-%EC%BA%90%EB%A6%AD%ED%84%B0%EC%85%8B-%EC%A7%80%EC%A0%95%ED%95%98%EC%97%AC-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0/](https://www.enteroa.com/2016/01/26/database-create-%EB%AC%B8%EC%97%90%EC%84%9C-%EC%BA%90%EB%A6%AD%ED%84%B0%EC%85%8B-%EC%A7%80%EC%A0%95%ED%95%98%EC%97%AC-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0/) : DB생성 시 캐릭터셋<br>

<br>
<br>
<br>
<br>
<br>
<참고><br>
1. 테이블명 대소문자 구분 시<br>
   - 테이블이 있음에도 테이블명에 대해 대소문자를 구분하여, 테이블이 없다고 할 때가 존재
   - 설정 확인 show variables like 'lower_case_table_names;' 값이 0일 경우 대소문자 구분, 1일 경우 구분 안함
   - 0일 경우, my.cnf 파일 편집<br>
     [mysqld] 영역 부분에 lower_case_table_names=1로 추가 또는 변경
   - DB 재기동<br><br>


2. hierarchical data Query
   - [https://m.blog.naver.com/PostView.nhn?blogId=agapeuni&logNo=60174661589&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F](https://m.blog.naver.com/PostView.nhn?blogId=agapeuni&logNo=60174661589&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F)
   - [http://www.gnujava.com/board/article_view.jsp?article_no=1853&menu_cd=29&idx_notice=NOTICE_FLAG+DESC%2C&board_no=16](http://www.gnujava.com/board/article_view.jsp?article_no=1853&menu_cd=29&idx_notice=NOTICE_FLAG+DESC%2C&board_no=16)
   - pssql : [http://blog.duveen.me/14](http://blog.duveen.me/14), [http://blog.duveen.me/13](http://blog.duveen.me/13)
   - plsql : [https://m.blog.naver.com/PostView.nhn?blogId=callsonda&logNo=220343710713&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F](https://m.blog.naver.com/PostView.nhn?blogId=callsonda&logNo=220343710713&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F)
  <br>
  

3. Error log
   - DB서버 기동 error : [http://idchowto.com/?p=11107](http://idchowto.com/?p=11107)


4. 참고 자료
   - [https://sqlangeles.com/2018/01/11/mysql-mariadb-%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%8B%9C%EC%9E%91-%EC%A2%85%EB%A3%8C/](https://sqlangeles.com/2018/01/11/mysql-mariadb-%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%8B%9C%EC%9E%91-%EC%A2%85%EB%A3%8C/)
   - 로그 관리 : [http://linuxism.tistory.com/518](http://linuxism.tistory.com/518)

<br>

5. 암호화, 복호화 <br>
    Mysql에서 제공하는 암호화, 복호화 <br>
    삽입할 때에는 암호화된 데이터를 HEX로 변환시켜 넣고, 가져올 때는 HEX를 풀고 복호화한다. <br>
 
   - 단방향(보통 패스워드) <br> 
     INSERT INTO 테이블명 (필드명) VALUES (PASSWORD('암호화 할 내용')) <br>
 
   - 쌍방향  <br>
     INSERT INTO 테이블명 (필드명) VALUES (HEX(AES_ENCRYPT('문자열', '암호화 키'))); <br>
 
   - 복호화  <br>
     SELECT AES_DECRYPT(UNHEX(필드명), '암호화 키') FROM 테이블명; <br>
     컬럼 타입이 varchar 일 경우 :  SELECT CAST(AES_DECRYPT(UNHEX(필드명), '암호화 키') AS CHAR) FROM 테이블명; <br>

6. SQL 특수문자 자체를 검색하기 <br>
   - [http://www.sqler.com/bColumn/493557](http://www.sqler.com/bColumn/493557) <br>

 <br><br>
 
7. 외부에서 접속이 안 된다면<br>
   - 방화벽 체크<br>
     firewall-cmd --permanent --zone=public --add-port=3306/tcp  // 설정 <br>
     firewall-cmd --reload  // 설정 reload <br>
     
8. @@DATEFIRST(Transact-SQL) | Microsoft Docs <br>
Clipped from: [https://docs.microsoft.com/ko-kr/sql/t-sql/functions/datefirst-transact-sql?view=sql-server-2017](https://docs.microsoft.com/ko-kr/sql/t-sql/functions/datefirst-transact-sql?view=sql-server-2017)<br>
적용 대상: SQL Server(2008부터)<br>
Azure SQL Database  <br>
Azure SQL Data Warehouse  <br>
병렬 데이터 웨어하우스 APPLIES TO:  <br>
SQL Server (starting with 2008)  <br>
Azure SQL Database  <br>
Azure SQL Data Warehouse  <br>
Parallel Data Warehouse  <br>
이 함수는 특정 세션에 대해 SET DATEFIRST의 현재 값을 반환합니다.This function returns the current value of SET DATEFIRST, for a specific session. <br>

모든 Transact-SQLTransact-SQL의 날짜 및 시간 데이터 형식 및 함수에 대한 개요는 날짜 및 시간 데이터 형식 및 함수(Transact-SQL)을 참조하세요.See Date and Time Data Types and Functions (Transact-SQL) for an overview of all Transact-SQLTransact-SQL date and time data types and functions. <br>
<br>
반환 형식Return Type <br>
tinyinttinyint <br><br>

RemarksRemarks <br>
SET DATEFIRST n은 주에서 첫 번째 일을 지정합니다(일요일, 월요일, 화요일 등).SET DATEFIRST n specifies the first day (SUNDAY, MONDAY, TUESDAY, etc.) of the week. n 값의 범위는 1에서 7입니다.The value of n ranges from 1 to 7. <br><br>

SQL  <br>
SET DATEFIRST 3; <br>
GO   <br>
SELECT @@DATEFIRST; -- 3 (Wednesday) <br>
GO <br><br>
 
미국의 경우 영어 환경은 @@DATEFIRST 기본값을 7(일요일)로 설정합니다.For a U.S. English environment, @@DATEFIRST defaults to 7 (Sunday). <br>

이 언어 설정은 SQL Server가 해당 문자열을 데이터베이스 저장소에 대한 날짜 값으로 변환하므로 문자열 해석에 영향을 줍니다.This language setting impacts character string interpretation as SQL Server converts those strings to date values for database storage. 이 설정은 데이터베이스에 저장된 날짜 값의 표시에도 영향을 줍니다.This setting also impacts display of date values stored in the database. 이 설정은 날짜 데이터의 저장소 형식에는 영향을 주지 않습니다.This setting does not impact the storage format of date data. <br>

이 예제에서는 먼저 언어를 Italian로 설정합니다.This example first sets the language to Italian. SELECT @@DATEFIRST; 문은 1을 반환합니다.The statement SELECT @@DATEFIRST; returns 1. 다음 명령문은 언어를 us_english로 설정합니다.The next statement sets the language to is then set to us_english. 마지막 명령문 SELECT @@DATEFIRST;는 7을 반환합니다.The final statement, SELECT @@DATEFIRST; returns 7. <br><br>

SQL  <br>
SET LANGUAGE Italian;   <br>
GO   <br>
SELECT @@DATEFIRST;   <br>
GO   <br>
SET LANGUAGE us_english;   <br>
GO   <br>
SELECT @@DATEFIRST;   <br><br>
 
예Examples <br>

이 예에서는 주의 시작 요일을 5(금요일)로 설정하고 현재 날짜인 Today를 토요일로 가정합니다.This example sets the first day of the week to 5 (Friday), and assumes that the current day, Today, falls on Saturday. SELECT 문은 주의 현재 날짜의 DATEFIRST 값과 현재 날짜 번호를 반환합니다.The SELECT statement returns the DATEFIRST value and the number of the current day of the week. <br><br>

SQL  <br>

SET DATEFIRST 5;   <br>
SELECT @@DATEFIRST AS 'First Day'   <br>
    ,DATEPART(dw, SYSDATETIME()) AS 'Today';   <br>
 

결과 집합은 다음과 같습니다.Here is the result set.  <br><br>

SQL  <br>

First Day         Today   <br>
----------------  --------------   <br>
5                 2   <br><br>
 

예제Example <br>

Azure SQL 데이터 웨어하우스Azure SQL Data Warehouse 및 병렬 데이터 웨어하우스Parallel Data Warehouse and 병렬 데이터 웨어하우스Parallel Data Warehouse  <br><br>

SQL  <br>

SELECT @@DATEFIRST;   <br><br>
 

관련 항목:See also <br>

구성 함수(Transact-SQL)Configuration Functions (Transact-SQL) 
