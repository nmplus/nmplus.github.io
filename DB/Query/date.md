# 날짜 계산

1. 오라클 to_date 사용. <br>
to_date를 사용하여 계산 할 경우, 결과값은 number 형식으로 나오게 되며, 일을 기준으로 계산된다.   <br>
a.  select to_date('20180709100000', 'yyyymmddhh24miss') - to_date('20180609100000', 'yyyymmddhh24miss') from dual;  <br>
    결과 : 30    --> 월이 한 달 전.  <br>
b. select to_date('20180609100000', 'yyyymmddhh24miss') - to_date('20180608100000', 'yyyymmddhh24miss') from dual;  <br>
    결과 : 1     --> 하루 전  <br>
c. select to_date('20180609110000', 'yyyymmddhh24miss') - to_date('20180609100000', 'yyyymmddhh24miss') from dual;  <br>
    결과 : 0.4616666666~~~    --> 1시간 전. 일을 기준으로 하기 때문에 시간은 소수점으로 계산되어 나오게 된다. 이 때는 24를 곱하여 시간으로 계산하면 된다.   <br>
                                               동일하게. 분을 알고 싶다면 * 60을 더하면 된다.  <br> <br>
 
[http://itpsolver.com/%EC%98%A4%EB%9D%BC%ED%81%B4-%EB%82%A0%EC%A7%9C-%EA%B4%80%EB%A0%A8-%ED%95%A8%EC%88%98-%EB%85%84-%EC%9B%94-%EC%9D%BC-%EB%8D%94%ED%95%98%EA%B8%B0-%EB%B9%BC%EA%B8%B0-%EB%93%B1%EB%93%B1/](http://itpsolver.com/%EC%98%A4%EB%9D%BC%ED%81%B4-%EB%82%A0%EC%A7%9C-%EA%B4%80%EB%A0%A8-%ED%95%A8%EC%88%98-%EB%85%84-%EC%9B%94-%EC%9D%BC-%EB%8D%94%ED%95%98%EA%B8%B0-%EB%B9%BC%EA%B8%B0-%EB%93%B1%EB%93%B1/)<br>

2. connect by [http://wiki.gurubee.net/pages/viewpage.action?pageId=27427825](http://wiki.gurubee.net/pages/viewpage.action?pageId=27427825)
 
