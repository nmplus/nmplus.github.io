# optimizer

SQL 문장의 최적화와 최적화 방법. <br><br>

  1) 규칙기반의 최적화 - RBO (Rule Based Optimization). <br>

 

     ORACLE이 정의하고 있는 우선 순위를 기반으로 해서 문장 수행의 과정을 정의한다.<br> 

     기본적인 방법이라는 장점이 있으나 ORACLE이 정의하고 있는 우선 순위가 항상 최적화 되어있지 않을 수 있다는 변수를 갖고 있다는 단점이 존재한다. <br>

 

     - ORACLE이 정의하는 RBO 기반 처리 우선순위표. <br>
   ![optimizer](https://user-images.githubusercontent.com/39476251/112588469-ce983780-8e42-11eb-9d17-7368280fe645.JPG)<br>
   
       - Session 레벨의 최적화 관련 환경변수 설정을 이용하여 규칙기반의 최적화를 설정하기 위한 명령은 다음과 같다. <br>

       . Alter Session Set Optimizer_Mode = 'Rule' 

       SQL> alter session set optimizer_mode = 'rule' ; 

       Session altered. 

       SQL> select strcuid, strouid, dateproc, strtprocno from ecommloginfo ; 

       STRCUID   STROUID   DATEPROC STRTPR 

       ---------- ---------- --------    ------ 

       INTERPK    NATE1124   20020101 

       INTERPK    WINKER71   20020101 

       INTERPK    NATE1124   20000110 

       INTERPK    GORA99     20000104  000002 

 

       4 rows selected. 

 

       Execution Plan 

       ---------------------------------------------------------- 

       0      SELECT STATEMENT Optimizer=RULE 

       1    0   TABLE ACCESS (FULL) OF 'ECOMMLOGINFO' 

       Statistics 

       ------------------------------------------------------- 

              0  recursive calls 

              4  db block gets 

              2  consistent gets 

              0  physical reads 

              0  redo size 

           1721  bytes sent via SQL*Net to client 

            700  bytes received via SQL*Net from client 

              4  SQL*Net roundtrips to/from client 

              1  sorts (memory) 

              0  sorts (disk) 

              9  rows processed 

  
