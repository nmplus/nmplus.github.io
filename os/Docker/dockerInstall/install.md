## CentOS8에 Docker 설치하기 (2021.03.30)

 ```
#Install
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce -y

#version 확인
docker version

#Docker 서비스 실행(daemon으로 백그라운드에 띄움)
sudo service docker start
 
#부팅시 자동 실행 설정 (reboot 후 ps -ef|grep docker 확인)
sudo chkconfig docker on

 ``` 

-  설치 후 docker version 명령어로 정상적으로 설치되었는지 확인 할수있다.    

![버전확인](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/os/Docker/dockerInstall/2.PNG)  

- docker-compose 설치는 아래 경로에서 대상이되는OS의 설치 가이드를 따라 진행한다.
https://docs.docker.com/compose/install/
```
# 리눅스에서 docker-compose 설치 및 실행권한 추가, 버전확인
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.6/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose -v
```
```
# docer-compose -v 허가거부시(실행권한이 안먹을 경우)
chmod 777 /usr/local/bin/docker-compose
```


#### user계정에서 sudo 명령어(root권한)를 사용시 아래와 같이 추가해야됨.  

0. 계정에 권한이 없는경우 아래 메세지 출력됨  
        "xxx는 sudoers설정 파일에 없습니다. 이 시도를 보고합니다."  

1. su -  root로 접근  
2. /etc/sudoers파일 열기  
        visudo -f /etc/sudoers
```
        ....생략

        ## User Aliases
        ## These aren't often necessary, as you can use regular groups
        ## (ie, from files, LDAP, NIS, etc) in this file - just use %groupname
        ## rather than USERALIAS
        # User_Alias ADMINS = jsmith, mikem

        #20라인 아래 특정 사용자의 계정에 sudo 권한을 부여함.
        # {대상계정}    ALL=(ALL)   ALL 
        ing   ALL=(ALL) ALL

        ...생략
```
  
3. 저장 후 해당계정에서 sudo 명령어 사용해 본다.  



#### root계정에서 Docker 설치할경우 user권한에서 명령어 수행시 Permisstion denied 발생

- 실행하고자하는 계정에 docker group 권한을 주어야 해당계정에서 docker를 사용할 수있음.

```
ex) ing 계정에 group 추가
  sudo /usr/sbin/groupadd -f docker
  groups
  sudo usermod -a -G docker ing
  세션종료 후 ing계정으로 로그인
  sudo service docker restart
```