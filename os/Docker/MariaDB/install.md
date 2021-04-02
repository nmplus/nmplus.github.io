## Docker를 사용한 MariaDB 설치

##### Docker가 설치 되었다면 아래 0~7 단계별 MariaDB 설치 부터 Tool로 접속 test 진행

0. MariaDB image를 내려받는다.
- 버전을 작성하지않으면 latest 버전을 받게됩니다.
  ```
  docker pull mariadb  
  ```
  ```
  docker pull mariadb:10.5.9
  ```
1. MariaDB 컨테이너 생성 (0번 생략시 docker run명령어실행시 image 다운로드됨)  
- docker run --help 참고
  ```
  docker run -d --name mdb -p 13306:3306 \
    -e MYSQL_ROOT_PASSWORD=test \
    -v /home/ing/docker/mariadb/mysql/my.cnf:/etc/mysql/my.cnf mariadb
  ```

- -d 속성 : container를 백그라운드 상태로 실행
- 컨테이너 명칭지정 : mdb (container Id의 Alias 형태로 사용됨)
- port : 13306 (container에서 사용중인 port를 host의 port에 포워딩 처리)
- -e 속성 : container에서 사용될 환경변수로 mariadb root 패스워드를 test로 설정함
- -v 속성 : Volume속성으로 host경로의 my.cnf파일 container의 파일과 마운트하여 설정파일을 재사용함
    - /var/lib/mysql경로를 mount하게되면 mysql데이터를 host에서 관리하게 되어 db백업이가능함.( mariaDB를 재설치 하여도 데이터는 그대로 보관됨)
    - ##### 근데 docker에서 두개파일 volume지정을 어떻게 하는거지??

- my.cnf파일 추가
  - 초기 characterset이 latin1로 되어있으며 utf8변경 해준다.
  - 
  ```
  [client]
  default-character-set = utf8mb4

  [mysql]
  default-character-set = utf8mb4

  [mysqld]
  character-set-client-handshake = FALSE
  character-set-server = utf8mb4
  collation-server = utf8mb4_unicode_ci
  ```
2. docker 프로세서 확인
- MariaDB가 제대로 설치 되었는지 상태값 등 확인
  ```
  docker ps -a
  ```

3. docker Container 접근 명령어
- 2번에서 container id를 알수 있다.
- docker exec -it 명령어를 통해 container 내부로 접근 할 수있다.
  ```
  docker exec -it {container id 또는 container name} /bin/bash
  ```
4. mariadb 접속
- docker run 명령어(1번 확인) 수행시 root 패스워드를 설정하였으며 아래 명령어 수행후 패스워드를 입력한다.
  ```
  mysql -uroot -p
  ```       
- mysql 설정 값 확인
  ```
  status
  ```
- database 생성/확인/접속
  - 생성후 해당 db로 접속 한다.
  ```
  create database nmdb;
  show databases;
  use nmdb;
  ```
5. user생성/권한설정/권한적용
- 외부에서 접속가능한 계정을 생성해야되므로 '%'로 계정을 생성함
    - create user ‘아이디'@'%' identified by ‘비밀번호'
-  권한설정  
    - grant all privileges on DB명.테이블명 to USER명
    - \*은 전체를 말함
    ```
    create user 'nmplus'@'%' identified by 'nmplus';
    grant all privileges on *.* to 'nmplus';
    flush privileges;
    ```

6. 시간설정
  - MariaDB를 빠져나와 linux에서 명령어 수행  
    ```
    timedatectl set-timezone 'Asia/Seoul'  
    ```
  - MariaDB 재기동(host에서 수행하세요.)
    ```
    docker restart {container id 또는 container name}
    ```
  - 다시 MariaDB 접속 후 아래 명령어로 현재시간을 확인한다.
    ```
    select now();
    ```
7. Tool로 접속
  - https://nmplus.github.io/DB/MariaDB/DBeaverTool.html


91. Docker log확인
    ```
    docker logs -f --tail=10 {container id 또는 container name}
    ```

92. MariaDB 중지/시작/재시작
- my.cnf 파일 수정, 시간설정 등으로 인해 재기동이 필요한 경우  
  ```
  docker stop {container id 또는 container name}
  docker start {container id 또는 container name}
  docker restart {container id 또는 container name}
  ```
