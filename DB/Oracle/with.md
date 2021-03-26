# with 구문

1. with 구문 내의 쿼리(subquery)의 결과가 여러 번 사용 될 때 유용. <br>

2. subquery 블록에 이름을 지정할 수 있게 함.  <br>

3. oracle Optimizer 는 with 구문은 inline View 또는 임시 테이블로 간주한다.  <br>

4. Oracle 9 이상 지원.  <br>

5. Oracle에서만 지원하는 기능.  <br>

6. 구문   <br>
with alias_nm as ( subquery )  <br>
select * from alias_nm;  <br>

7. subquery 가 2개 이상이 필요할 경우 구문  <br>
with alias_nm1 as ( subquery )  <br>
     , alias_nm2 as ( subquery )    <br>
      ….  <br>
select * from alias_nm1, alias_nm2 
