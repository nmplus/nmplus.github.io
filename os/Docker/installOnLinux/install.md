# CentOS8에 Docker 설치하기 (2021.03.30)

설치는 명령어 한줄로 간단하게 설치가 끝난다.

 ```
#Install
sudo yum install docker
 
#Docker 서비스 실행
sudo service docker start
 
#부팅시 자동 실행 설정
sudo chkconfig docker on
  
 ```

설치 후 docker version 명령어로 정상적으로 설치되었는지 확인 할수있다.

![설치](./os/Docker/installOnLinux/1.PNG)

![버전확인](./os/Docker/installOnLinux/2.PNG)