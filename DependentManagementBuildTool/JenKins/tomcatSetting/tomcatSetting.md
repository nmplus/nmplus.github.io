# Tomcat 설치  
  
1. 다운로드  
    https://tomcat.apache.org/download-80.cgi  
    http://apache.mirror.cdnetworks.com/tomcat/tomcat-8/v8.5.42/bin/apache-tomcat-8.5.42.tar.gz 
    8.5.42  Core   tar.gz 로 다운로드 받는다. ( java 버전에 따라 선택 )  
  
2. centos 서버에 복사한다.   
  
3. 압축을 해제한다.   
    tar -xvzf apache-tomcat-8.5.42.tar.gz   
  
4. 실제 tomcat을 설치 할 위치로 이동 또는 복사한다.   
````
cp apache-tomcat-8.5.42.tar.gz /usr/local/apache-tomcat-8.5.42 
````
  

5. 명칭을 간단하게 심볼릭 링크를 하나 생성해 준다.   
````
ln -s apache-tomcat-8.5.42 tomcat 
````
  
6. 방화벽을 해제한다.   
````
iptables -I INPUT 1 -p tcp --dport 8080 -j ACCEPT   
iptables -I OUTPUT 1 -p tcp --dport 8080 -j ACCEPT  
````
   

7. 정책을 저장한다.   
````
service iptables save  
````
  

8. 서비스를 재시작한다.  
````
service iptables restart 
````
  