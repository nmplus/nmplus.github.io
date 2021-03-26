# Tools 설치  

1. JDK 설치   
oracle 설치 된 것으로 파악.  
2. maven 설치  
https://maven.apache.org/download.cgi  
페이지에서  apache-maven-3.6.1-bin.tar.gz 파일 다운로드.  
src는 소스코드이므로, 제외.  
3. 실제 설치 될 서버로 복사( 임시 경로 )  
4. 압축 해제  
tar xvzf <파일명>  
$ apache-maven-3.6.1-bin.tar.gz  
5. 압축 해제한 폴더를 실제 사용할 위치로 이동시킨다  
mv <폴더명> <이동할 폴더경로:root부터 작성>  
$ mv apache-maven-3.6.1 /usr/local  
6. 해당 폴더로 이동  
cd <이동한 폴더경로:root부터 작성>  
$ cd /usr/local  
7. 경로명이 기니, 링크 생성.  
ln -s <폴더명> maven  
$ ln -s apache-maven-3.6.1 maven  
8. 환경 변수 설정을 한다.  
$ vi /etc/profile.d/maven.sh  
maven.sh 라는 파일명은 임의의 파일명으로 별도의 인식가능한 파일로 생성해도 좋다.  
이렇게 생성하면, Global로 설정된다.  
참고 : yum으로 설치할 경우, /etc/profile 에 자동으로 추가한다.  
9. maven.sh 파일 내부에 내용을 작성한다.  

```   
export MAVEN_HOME=/usr/local/maven 

export PATH=$PATH:$MAVEN_HOME/bin 
```  
  
10. 재로그인하여, 환경설정이 제대로 되었는지, 제대로 동작하는지 확인한다.  
````
$ mvn -version  
````
11. maven local repository를 설정해 준다.  
vi <maven설치경로>/conf/settings.xml  
$ vi /usr/local/maven/conf/settings.xml  
12. settings.xml 파일 내의 localRepository 설정 부분을 주석 해제하고 경로를 맞춰준다.  
<localRepository>/usr/local/.m2/repository</localRepository>  
경로는 기본적으로 <해당계정>/.m2/repository 로 설정되므로,  
같은 계정이거나, 젠킨스 계정과 동일하거나 하는 경우에는 그대로 사용해도 된다.  
13. local Repository에 jar 파일들을 복사한다.  
centos 서버는 인터넷이 되지 않으므로, 해당 경로의 jar 파일들을 이용하여 build된다.  

