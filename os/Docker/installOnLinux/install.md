# CentOS 8에 Docker 설치하기 (2021.03.30)


설치는 user 권한에서 수행하는 가이드입니다.  

기본적으로 docker가 root 권한을 요구하기때문에 해당 user를 docker 그룹에 추가합니다.

group 추가
 ```
#Install
sudo yum install docker
 
#Docker 서비스 실행
sudo service docker start
 
#부팅시 자동 실행 설정
sudo chkconfig docker on
  
 ```

