## CentOS8에 Docker 설치하기 (2021.03.30)

 ```
#Install
sudo yum install docker
 
#Docker 서비스 실행
sudo service docker start
 
#부팅시 자동 실행 설정
sudo chkconfig docker on
  
 ```

- 설치는 명령어 한줄로 간단하게 설치가 끝난다.    

![설치](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/os/Docker/dockerInstall/1.PNG)  

-  설치 후 docker version 명령어로 정상적으로 설치되었는지 확인 할수있다.    

![버전확인](https://raw.githubusercontent.com/nmplus/nmplus.github.io/main/os/Docker/dockerInstall/2.PNG)  

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



