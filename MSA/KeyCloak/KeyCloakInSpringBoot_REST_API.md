# Spring boot에 KeyCloak 로그인 적용  

- 참고 사이트 : https://ichi.pro/ko/keycloak-eulo-spring-boot-rest-api-boan-2024551874638  

- keycloak 콘솔 로그인 http://192.168.1.23:8888/  

1. realm 추가  
    - 'Name'을 추가 후 생성한다.  
    - realm은 Master가 처음 생성되어 있으며 추가되는 realm을 관리하는 역할을 한다.  
    - realm은 Client간 SSO를 공유할 수 있다. 그러므로 MSA 구현시 realm영역으로 인증, 인가의 범위가 됨.  
    - tokens 탭에서 'Access Token Lifespan' 이 기본 5분으로 잡혀있다.

2. client 추가  
    - 'Client ID'를 추가 후 생성한다.  
    - Setting 탭 설정. Access Type은 confidential 그리고 ServiceAccounts Enabled, Authorization Enabled은 ON으로 스위치 변경.  
    - Valid Redirect URIs는 http://192.168.1.23:8888/* 설정 후 저장. Credentials 탭에서 Secret 값을 확인할 수 있다.  
    - Roles 탭을 선택해서 role을 추가한다.  
    
3. User 추가  
    - Users 탭에서 Adduser 선택. 'Username' 입력 후 저장. 그리고 Credentials 탭에서 패스워드를 입력후 SetPassword 선택  
    - User가 생성되었으며 redirect 로그인 방식은 로그인 후 비밀번호를 변경하는 ui로 넘어가게되지만 restAPI방식은   
    변경하는 방법이 확인이 좀더 필요하다.   
    (2021.04.27 해당user의 details탭에서 Update Password 버튼의 x를 눌러 'Required User Actions'을 없애 버린다.)  
    - Role Mappings 탭에서 Client Roles의 클라이언트 명을 선택 후 role을 추가한다.  
4. token 생성 url 확인  
    -   Realm Setting > General탭에서 Endpoints의 OpenID Endpoint Configuration 선택시 새창에서 token_endpoint를 확인할수 있다.  
    ex) "token_endpoint": "http://192.168.1.23:8888/auth/realms/NMP_test/protocol/openid-connect/token"  

5. accessToken 생성 
    - postman등으로 token_endpoint에 토큰생성 요청호출  
    ```
    url : http://192.168.1.23:8888/auth/realms/NMP_test/protocol/openid-connect/token
    Content-Type: application/x-www-form-urlencoded'
    POST방식
    parameter(body)
        grant_type : password
        client_id : <CLIENT_ID>
        client_secret:<CLIENT_SECRET>
        username:<USERNAME>
        password:<PASSWORD>
    ```  

6. accessToken 재생성  
    - url은 동일하며 새로생성한 accessToken과 refreshToken을 발급받는다.
    - accessToken은 만료시간은 기본설정 5분이며 refreshToken은 30분이다.

    ```
    url : http://192.168.1.23:8888/auth/realms/NMP_test/protocol/openid-connect/token
    Content-Type: application/x-www-form-urlencoded'
    POST방식
    parameter(body)
        grant_type : refres_token
        client_id : <CLIENT_ID>
        client_secret:<CLIENT_SECRET>
        refres_token:<REFRESH_TOKEN>
    ```

7. spring boot 샘플가이드(예정)



#### 참고

![1](https://user-images.githubusercontent.com/81209685/116206184-8178ef80-a779-11eb-80ac-7697b25ae430.PNG)
![2](https://user-images.githubusercontent.com/81209685/116206185-82118600-a779-11eb-9f8b-db9180c6e1e6.PNG)
![3](https://user-images.githubusercontent.com/81209685/116206187-82aa1c80-a779-11eb-90af-d2354122dcc4.PNG)
![4](https://user-images.githubusercontent.com/81209685/116206188-82aa1c80-a779-11eb-8adf-0fbb24e1672d.PNG)
![5](https://user-images.githubusercontent.com/81209685/116206189-8342b300-a779-11eb-83b3-f58d640a8249.PNG)
![6](https://user-images.githubusercontent.com/81209685/116206191-8342b300-a779-11eb-92cd-8250c86c90a4.PNG)
![7](https://user-images.githubusercontent.com/81209685/116206192-83db4980-a779-11eb-8b11-50105e519815.PNG)
![8](https://user-images.githubusercontent.com/81209685/116206194-83db4980-a779-11eb-9815-6c7d4066c1ec.PNG)
![9](https://user-images.githubusercontent.com/81209685/116206195-8473e000-a779-11eb-9d6e-57bd1c2d40a3.PNG)
![10](https://user-images.githubusercontent.com/81209685/116206196-8473e000-a779-11eb-822d-98ec8f6fec5f.PNG)
![11](https://user-images.githubusercontent.com/81209685/116206198-850c7680-a779-11eb-8a07-e75b037a5a6b.PNG)
![12](https://user-images.githubusercontent.com/81209685/116206199-850c7680-a779-11eb-969c-a8ab0027bd85.PNG)
![13](https://user-images.githubusercontent.com/81209685/116206202-85a50d00-a779-11eb-96be-cfa233c8d8c8.PNG)
![14](https://user-images.githubusercontent.com/81209685/116206177-8047c280-a779-11eb-8f0d-7e9d6b15516f.PNG)
