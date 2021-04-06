
## Docker Compose를 사용한 MariaDB 설치

Docker와 docker-compose가 설치 되었다면 아래 0~7 단계별 MariaDB 설치 부터 Tool로 접속 test 진행

0. MariaDB image를 내려받는다.
- 버전을 작성하지 않으면 latest 버전을 받게됩니다.
- 이미 image를 내려받았거나 docker run명령어시 image를 받을수도 있다.
  ```
  docker pull mariadb  
  ```
  ```
  docker pull mariadb:10.5.9
  ```
1. 설치전 준비사항
  - docker-compose.yml 파일과 볼륨으로 지정할 폴더를 생성함.
  ```
  /home/본인계정/docker/
  ㄴ docker-compose.yml   # docker-compose 설정
  ㄴ mariadb/config       # mariadb 설정
  ㄴ mariadb/data         # mariadb데이타 저장소 지정

  ```

2. my.cnf파일 생성
  - /home/본인계정/docker/mariadb/config폴더에 아래내용추가
  - mariadb는 latin1 언어가 기본이며 utf8mb4로 변경한다.
  ```
  [mysql]
  default-character-set = utf8mb4

  [mysqldump]
  default-character-set = utf8mb4

  [mysqld]
  #timezone
  default-time-zone = '+9:00'

  #character
  character-set-client-handshake = FALSE
  character-set-server = utf8mb4
  collation-server = utf8mb4_unicode_ci
  init_connect                    = set collation_connection=utf8mb4_general_ci
  init_connect                    = set names utf8mb4
   ```
3. docker-compose.yml 생성
- yml확장자는 YAML언어로 xml, json과 같이 쉽게 접근할수있는 직렬화 언어이며 콜론과 공백사용으로 키와 값을 표현함.
- 아래는 docker-compose양식으로 mariadb설정을 작성한내용이다.
- 참고 https://docs.docker.com/compose/gettingstarted/
```
vi docker-compose.yml

version : '3'
services:
  db:
    container_name: mariadb
    image: mariadb:latest
    restart: always
    ports:
      - 3306:3306
    volumes:
      - /home/ing/docker/mariadb/data:/var/lib/mysql
      - /home/ing/docker/mariadb/config:/etc/mysql/conf.d
    environment:
      MYSQL_ROOT_PASSWORD: test
```

4. 실행, 상태확인 등
- 실행은 docker-compose.yml 경로또는 그 하위에서 실행가능
```
docker-compose up -d
```
- 확인은 docker ps -a 명령어의 docker-compose 버전
  - docker 명령어로 stop/start 상태도 동일하게 확인됨
```
docker-compose ps
```
- 중지/시작/제거
```
docker-compose stop
docker-compose start
docker-compose down
```
