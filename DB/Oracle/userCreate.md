#유저생성

1. SYSDBA 또는 SYSTEM 계정으로 로그인 <br>

2. 유저 생성 <br>

         sql : create user c##wowsom identified by ws1q2w3e;

   - tablespace 생성 <br>
http://lee-mandu.tistory.com/229 <br>
http://pentode.tistory.com/196 <br>
http://12bme.tistory.com/300 <br>

   - 유저 잠금 풀고 TS 및 권한 부여 <br>

 

     -> 12C 부터는 공통 사용자 생성 시 c##을 유저명 앞에 붙여줘야만 한다. 안 그럴 경우, 에러 발생. c##은 대소문자 구분한다. 여기서는 소문자 <br>
    ( ex.  nmplus  유저명이라면 c##nmplus ),  <br>
     -> Oracle Standard Edition Two 12.1.0.2.v12 ==> AWS에서 설치한 oracle에서는 c##... 붙이니 안 됨. 12C는 맞을텐데… 왜지? <br>
     -> 싫다면, sysdba로 접근하여, <br>
    alter session set "_ORACLE_SCRIPT"=true; 를 해 주면 기존과 동일하게 가능. <br>
    원격 클라이언트를 이용해서는 안 되는듯하다. 해당 local에서 작업 할 것. <br><br>

 

 

>    sqlplus "/as sysdba" <br>
SQL> alter session set "_ORACLE_SCRIPT"=true; <br>
세션이 변경되었습니다. <br><br>

 

-- 유저 생성 <br>

-- 12c부터 추가 된 것.C##이 없으면 생성 시 에러. <br>
SQL> create user wowsom identified by ws1q2w3e; <br>
사용자가 생성되었습니다. <br><br>

 
-- tablespace 생성 <br>
CREATE TABLESPACE TSWSM <br>

    DATAFILE 'C:\app\nmp\oradata\TSWSM' SIZE 200M -- size {int} [K|M] <br>

    AUTOEXTEND ON NEXT 5M --  MAXSIZE 200M;       // 5M씩 최대 200M까지 자동 증가 200M가 다차면 에러발생 <br><br>



-- 계정 잠금 해제 <br>
SQL> alter user wowsom account unlock; <br>
사용자가 변경되었습니다.  <br><br>


-- 로그인 및 테이블 생성 권한 부여.  resource 권한은 create 만 가지고 있음. ( insert  불가 ) <br>
SQL> grant connect, resource to wowsom; <br>
권한이 부여되었습니다. <br><br>


-- insert 등에 대해 가능하도록 권한 부여. <br>
SQL> alter user wowsom default tablespace users quota unlimited on users; <br>
사용자가 변경되었습니다. 
