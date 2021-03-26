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

  
 2) 비용기반의 최적화 - CBO (Cost Based Optimization). 

 

     통계자료를 기반으로 하여 문장 수행의 우선순위를 결정하므로 가장 정확한 최적화 기 

     법으로 선택되어지고 있다. 그러나, 통계자료를 만들어 준다는 일이 항상 최신의 통계 

     정보를 구축해 놓아야 한다는 부담으로 존재한다는 단점을 들 수 있다. 

 

     - Session 레벨의 최적화 관련 환경변수 설정을 이용하여 비용기반의 최적화를 설정 

       하기 위한 명령은 다음과 같다. 

       . Alter Session Set Optimizer_Mode = Choose 

         위의 명령은 SQL 문장을 수행함에 있어서 비용기반의 최적화를 지정한다. 

       . Alter Session Set Optimizer_Mode = First_Row 

         위의 명령은 SQL 문장을 수행함에 있어서 비용기반의 최적화를 수행하며 특히, 

         명령수행의 첫 Response에 중점을 둔다. 

       . Alter Session Set Optimizer_Mode = All_Row 

         위의 명령은 SQL 문장을 수행함에 있어서 비용기반의 최적화를 수행하며 특히, 

         명령수행의 전체 Response에 중점을 둔다. 

 

     - 비용기반의 최적화를 위한 통계 정보의 구축. 

       . Analyze Table table_name Compute Statistics 

         지정한 테이블에 대한 전체의 통계를 구축한다. 

       . Analyze Table table_name Estimate Statistics 

         지정한 테이블에 대해 비율적 통계를 구축한다. Compute Statistic으로 생성한 통 

         계에 비해서는 다소 정확도가 떨어질 수 있으나 생성속도가 빠르고 그 생성속도에 

 

         비해서 상당히 정확한 통계를 구축한다. 

       . Analyze Table table_name Delete Statistics 

         구축되어 있는 통계자료를 삭제한다. 새로운 통계자료를 구축하기 전에 필요한 과 

         정이다. 

 

     - 통계 정보를 구축한 후 비용기반의 최적화 실습. 

     SQL> analyze table ecommloginfo compute statistics for table for columns strcuid 

           size 20 ; 

     Table analyzed. 

     SQL> alter session set optimizer_mode = 'choose' ; 

     Session altered. 

     SQL> select strcuid, strouid, dateproc from ecommloginfo 

           2  where dateproc like '200001%' ; 

 

     STRCUID    STROUID    DATEPROC 

     ---------- ---------- -------- 

     INTERPK    WINKER71   20000110 

     INTERPK    NATE1124   20000110 

     INTERPK    GORA99     20000104 

 

     Execution Plan 

     ---------------------------------------------------------- 

     0      SELECT STATEMENT Optimizer=CHOOSE (Cost=1 Card=1 Bytes=26) 

     1    0   TABLE ACCESS (FULL) OF 'ECOMMLOGINFO' (Cost=1 Card=1 Bytes 

              =26) 

 

     Statistics 

     ---------------------------------------------------------- 

          0  recursive calls 

          4  db block gets 

          2  consistent gets 

          0  physical reads 

          0  redo size 

       1327  bytes sent via SQL*Net to client 

        718  bytes received via SQL*Net from client 

          4  SQL*Net roundtrips to/from client 

          1  sorts (memory) 

          0  sorts (disk) 

          3  rows processed 
