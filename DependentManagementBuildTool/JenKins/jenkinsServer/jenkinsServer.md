# jenkins 서버 기동
  
1. tomcat 하위로 jenkins.war 파일을 복사합니다.  
   이 때, war 파일의 압축을 해제하면 해당 폴더에 바로 풀리게 되므로,   
   폴더를 하나 생성해 준다.  
   mkdir <폴더경로>  
   mkdir /usr/local/tomcat/webapps/jenkins  
   cp <파일명> <경로>  
   cp jenkins.war /usr/local/tomcat/webapps/jenkins  
 
  
2. war 파일의 압축을 해제한다.  
   jar -xvf <압축파일명>  
   jar -xvf jenkins.war  
  
3. 복사 해 두었던 plugins 압축 파일을 압축 해제 한다.  
   tar -xvzf <압축파일명>  
   tar -xvzf plugins.tar.gz   
  
4. plugin 파일을 jenkins 폴더 하위로 이동시킨다.  
    mv <폴더명> <이동될 폴더명>  
    mv plugins ~~/usr/local/tomcat/webapps/jenkins~~  <사용자계정폴더>/.jenkins   
    --> NO!!!!!  
    plugin 등은 <사용자계정폴더>/.jenkins 하위에 복사해야 한다.  
    비밀번호 확인도 해당 위치에 있다.   
  
5. tomcat에 젠킨스를 설정해 준다.  
````  
vi /usr/local/tomcat/conf/server.xml 

<Host name="localhost"  appBase="/usr/local/tomcat/webapps/jenkins" unpackWARs="true" autoDeploy="true">   
    <Context path="/jenkins" docBase="." reloadable="true"/>   
</Host>  
````  
  
6. 접속  
   ip:port/jenkins 


