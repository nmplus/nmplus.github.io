# KeyCloak 설치 가이드


##### Docker Compose를 이용한 KeyCloak 설치

- https://www.keycloak.org/
- docker 설치가 선행되어야 합니다.

1. keycloak에서 제공하는 샘플
    - docker-compose로 설치하기위해 keycloak에서 제공하는 샘플yml을 사용합니다.
    - keycloak는 기본설치시 h2 db를 사용합니다.  
    그러므로 db를 연결해야하며 샘플에서 여러db와 연계하는 방법을 제공합니다.
    - 샘플 url
    ```
        https://github.com/keycloak/keycloak-containers/tree/master/docker-compose-examples
    ```

2. 적당한 장소에 폴더생성 후 명칭은 docker-compose.yml로 파일을생성합니다.

```
version: '3'

volumes:
  mysql_data:
      driver: local

services:
  mysql:
      image: mysql:5.7
      volumes:
        - mysql_data:/var/lib/mysql
      environment:
        MYSQL_ROOT_PASSWORD: root   #root패스워드 설정
        MYSQL_DATABASE: keycloak
        MYSQL_USER: keycloak
        MYSQL_PASSWORD: password
      ports:
        - 13306:3306                #외부에서 접근시 사용할 port지정
  keycloak:
      image: quay.io/keycloak/keycloak:latest
      environment:
        DB_VENDOR: MYSQL
        DB_ADDR: mysql
        DB_DATABASE: keycloak
        DB_USER: keycloak
        DB_PASSWORD: password
        KEYCLOAK_USER: admin                #keycloak 콘솔 접속 계정
        KEYCLOAK_PASSWORD: nmplus0220       #keycloak 콘솔 접속 비번
        #JDBC_PARAMS: "connectTimeout=30000"
      ports:
        - 8888:8080                         #keycloak 콘솔 접속 port
      depends_on:
        - mysql


```

3. 실행 및 확인
    - docker-compose.yml파일 위치에서 명령어 수행  
    ```
    docker-compose up -d
    ```
    - 실행 확인  
    ```
    docker ps -a
    ```
    - log확인 및 tail  
    ```
    dc logs -f --tail 5 컨테이너id또는 name
    ```

4. 콘솔 접속
    - http://192.168.1.23:8888/auth -> Administration Console 클릭 및 로그인  
    - admin / 비번은 회사내부정보
    


![auth](https://user-images.githubusercontent.com/81209685/116022738-bd328d00-a685-11eb-9cda-ce86cc575a90.PNG)  

![console](https://user-images.githubusercontent.com/81209685/116022608-75ac0100-a685-11eb-8409-90ad4db742d2.PNG)

