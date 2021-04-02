# Docker 가이드


##### docker 자주 쓰는 실행 명령어
````

docker run [options] IMAGE [COMMAND [ARG...]]

OPTIONS	   내용설명
-d	       detached mode로 백그라운드로 계속실행중인 상태.
           -d속성을 주지않으면 STATUS가 Exited로 됨. 호출시에만 동작하게됨
-p         host에 Container 포트 포워딩
-v         host에 Container 폴더 마운트
           ex) $ docker run -it -v (호스트 파일):(컨테이너의 파일) centos /bin/bash

-e         Container 내부에서 사용될 환경변수 설정
–name	   Container 이름설정(미 지정시 docker가 랜덤 생성)
````

##### 기본 사용 명령어
````
- Container 중지 (공백으로 구분해서 한번에 여러 Container중지가능)  
    docker stop [name 또는 Container id]  

- 이미지 목록  
    docker images  

- 이미지 삭제  
    docker rmi [image id]  

- 컨테이너 목록  
    docker ps -a  

- 컨테이너 삭제 (실행중일 경우 중지 후 삭제)
    docker rm [container id]  

% docker exec
    - docker exec -it {컨테이너명} {실행할 명령어}
    - 실행중인 docker에 명령을 실행
    ex) mariadb
        docker exec -it mariadb /bin/bash
        

% Volume는 Host와 Containerr간 폴더를 마운트 한다.  
    (설정, 백업경로 등을 Host에서 관리 할경우 Container가 추가/삭제되어도 재사용가능)
    - Volume 생성

    - Volume 조회

    - Volume 삭제


````






