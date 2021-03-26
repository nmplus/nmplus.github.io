# SVN 등록
  
1. 설정  
   project url은 중요하지 않다.  
  
![download](https://user-images.githubusercontent.com/24904435/112592982-356d1f00-8e4a-11eb-9e1e-490a91d08deb.png)  
  
  
2. SVN repository URL 셋팅  
  
![download](https://user-images.githubusercontent.com/24904435/112593388-c3490a00-8e4a-11eb-82bc-92627d6948ff.png)  
  
3. 빌드 유발이 가장 문제?라면 문제인데,  
   SVN에서는 pollscm을 써야 하는 것으로 파악.. 했으나, 상당 복잡.. ;ㅁ;  
   그냥 매일 밤에 빌드하는 형식으로만 등록 해 놓고, 나머지는 페이지에서 직접 돌리는 것으로… ;;  
   - Build Periodically를 체크  
   crontab 형식으로 지정한다.  
   분 | 시간 | 날짜 | 월 | 요일 | 명령  순.  명령은 생략 가능    
  
4. bulid 에서는 invoke top-level Maven tartgets 선택 후   
   build 스크립트 입력.  예)  clean install  
   build 후 조치에서 deploy to container 선택 ( deploy to container plugin 미설치 시 해당 선택 미표시 )  
   tomcat에 대한 credential은   
   tomcat-user.xml 에 추가 한 이후, 이를 이용하면 된다.  
   예)  
````   
  <role rolename="tomcat"/>  

  <role rolename="role1"/>  

  <user username="tomcat" password="<must-be-changed>" roles="tomcat"/>  

  <user username="both" password="<must-be-changed>" roles="tomcat,role1"/>  

  <user username="role1" password="<must-be-changed>" roles="role1"/>  

  <user username="jenkins" password="1q2w3e4r" roles="tomcatrole1"></user>    --> 추가 부분  
````
  
![download](https://user-images.githubusercontent.com/24904435/112593599-115e0d80-8e4b-11eb-8cb2-e4c1e4342e47.png)    
  
5. 참고.  
빌드 후 조치에 deploy 하면, war를 복사하여, 바로 redeploy를 하기 때문에,   
배포를 자주 하게 되면 메모리가 해제되지 않아, 나중에는 느려지거나, 최악의 경우, 서버가 멈출 수도 있다.  
  
이 경우에는, 빌드 step에 execute windows batch command 또는 execute shell 을 이용.  
./shutdown.sh => ./startup.sh 을 등록해 준다.  
또한, 이 때, 서버가 내려가는 시간을 기다려 줘야 하므로, timeout을 이용하여 잠시 대기 해 준다.  
윈도우 예시)     
````
set JAVA_HOME=D:\Java\jdk1.6  
  
cd "D:\Java\Tomcat 6" 

cmd /c bin\shutdown.bat 

timeout 5 

cmd /c bin\startup.bat   
````
  
6. 상당히 여러 방법이 있고, 오류도 다양하여,   
   적용 및 테스트를 거쳐야 할 듯.  
 
