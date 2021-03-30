# CentOS8에 Docker 설치하기 (2021.03.30)

 ```
#Install
sudo yum install docker
 
#Docker 서비스 실행
sudo service docker start
 
#부팅시 자동 실행 설정
sudo chkconfig docker on
  
 ```

#### 설치는 명령어 한줄로 간단하게 설치가 끝난다.    

![설치](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/os/Docker/installOnLinux/1.PNG)  

#### 설치 후 docker version 명령어로 정상적으로 설치되었는지 확인 할수있다.    

![버전확인](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/os/Docker/installOnLinux/2.PNG)  