# war 파일 만들기( feat. docker )  
  
plugin들은 젠킨스 웹서비스 안에서 인터넷으로 설치되도록 되어있다.  
인터넷이 불가하므로, 타시스템에서 원하는 plugin을 모두 설치한 후,  
jenkins 하위에 있는 plugin 폴더를 모두 복사하는 방법으로 설치해야 한다.  
docker로 하지 않고, 그냥 자신의 PC에 직접 설치해도 된다. g  
다만, 이 경우 재설치가 필요 할 경우, 번거로우니, Docker로 생성하였다.   

1. Docker 생성  
````
docker run -u root --name jenkinsWar -d -p 8088:8080 -p 50001:50001 -v C:/dev/docker/jenkinsWar:/var/jenkins_home jenkinsci/blueocean  
docker run -u root --name jenkinsWar -d -p 8088:8080 -p 50001:50001 -v /c/Users/bumsg/docker/jenkinsWar:/var/jenkins_home jenkinsci/blueocean  
````
  
  임의의 폴더로 설정했을 경우에는, 윈도우 계정에 접근해야 하므로, 윈도우 계정에 비번이 설정되어 있을 경우, 윈도우 계정 비번을 입력하라는 팝업창이 뜬다.  
  사용자 폴더 하위 일 경우에는, 경로 입력 시 맨 앞에 / 가 붙어야 하며, 계정 비번 입력 창은 뜨지 않는다.  
  
2. 이 때, firewall에 의해, 포트가 막혀있다면, 연결되지 않으므로, 방화벽을 확인 해 보자.  
  
3. 최초 비밀번호 확인  
````
docker exec -it jenkinsWar bash  
cat /var/jenkins_home/secrets/initialAdminPassword  
````
  
윈도우 일 경우에는 program files 폴더 밑이 기본 폴더이며, /secrets 이하는 동일하다.  

4. 브라우져에서 접속 
http://localhost:8088/  
최초 비밀번호 입력  

5. 이후, plugin 설치 화면에서는 기본 설정으로 설치 해 준다.  
Install suggested plugin 선택.   
클릭 시 바로 설치로 넘어간다  
  
6. 설치 후 관리자 계정을 생성한다.  
nmplus/nmp0220!@

  
![download](https://user-images.githubusercontent.com/24904435/112577642-14033780-8e38-11eb-8d6b-1bbe884cebaa.png)  
7. 이후, 접근 URL을 설정해 준다.  
변경 가능하나, 그대로 진행.  

![download](https://user-images.githubusercontent.com/24904435/112577936-b0c5d500-8e38-11eb-8645-4606ee98fd48.png)  
  
8. 재시작  
9. 로딩 화면이 변하지 않는다면, refresh.  
10. 로그인  
11. 설치된 plugin 업데이트 및 Deploy to container plugin 설치   
    war 배포를 위한 plugin  
12. plugin 폴더를 압축한다.  
    docker exec -it jenkinsWar bash  
    cd /var/jenkins_home  
    tar -cvzf plugins.tar.gz plugins  
13. jenkins 공식 war파일을 다운로드 한다.   
    http://mirrors.jenkins.io/war-stable/  
    이후, latest 경로 파일 다운로드.   
14. plugin 압축 파일 및 war 파일을 centos 서버에 복사한다.  