# DBeaver로 MariaDB접속

- 데이터베이스 > 새데이터베이스 연결 선택  
  새창이 나오며 선택할수 있는 database 목록이 뜬다. 여기서 MariaDB 클릭  

![1번](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/DB/MariaDB/1.PNG)  


- Host / port / Database / username / password 를 입력후 Test Connection버튼 클릭
정상적으로 접속 되거나 그림과 같이 Connection Timed out이 발생하기도 한다.    

![2번](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/DB/MariaDB/2.PNG)  


- 오류가 발생한 경우 SSH탭에서 MariaDB가 설치된 서버의 정보로 접속테스트를 해본다.(ssh port는 22번)  
  만약 SSH가 접속을 실패 하였다면 openssh설치부터 확인해봐야 한다.  
  SSH가 접속이 되지만 DB접속이 안되는 경우 접속정보를 잘못 작성했는지 또는 MariaDB의 외부접속 허용 권한을 등록했는지 확인이 필요함    


![3번](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/DB/MariaDB/3.PNG)  


![4번](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/DB/MariaDB/4.PNG)  
