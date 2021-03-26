# 접속테스트

1.오라클 서버가 설치된 컴퓨터. <br>
sqlplus 이후, SYSTEM / {password} <br>
따로 계정이 있다면 그를 이용해도 상관없으나, SYSTEM 계정은 default이므로 이를 이용. <br><br>

2. 하지만, 원격 접속은 안 될 경우가 있다. ( 사실 거의 대부분 안 될 것 ) <br>
- 원격접속 : 타PC에서 클라이언트 프로그램등을 이용해서 접근이 안 될 경우. <br>
  -> ora-12170 : 접속 시간 초과  <br><br>

 

http://tctt.tistory.com/73?category=648027   : 리스너 설정 <br>

 아니라면 방화벽 체크 <br>

윈도우10 : 앱 허용. tnslistnr 와 oracle 허용 <br><br>

 

cmd에서 확인(서버에서가 아닌 원격 접속 할 컴퓨터에서) : tnsping ip port  확인이 떨어지는지 확인    <br>
또는 tracert 아이피 를넣어서 연결이 되는지 확인 
