# Sequence 값 가져오기

-- 됨. <br>

select NVL(MAX(CNSTW_SEQ) + 1, 1)  <br>

  from ZLIDS_CNSTW_ORD_ALTR_HIS  <br>

 where CNSTW_ORD_NO = 'S01-20181018-R013'  <br>

;  <br> <br>

 

 

-- 안 됨.  <br>

select MAX(NVL(CNSTW_SEQ, 0)) + 1  <br>

  from ZLIDS_CNSTW_ORD_ALTR_HIS  <br>

 where CNSTW_ORD_NO = 'S01-20181018-R013'  <br>

;  <br> <br>

 

--> where 절에 따른 데이터가 없을 경우, 두 번째 쿼리의 경우, null  <br>

물론, 첫번째의 경우도 CNSTW_SEQ가 number라는 가정.  <br>

아니라면, 제대로 된 값이 나오지 않는다.  

 
