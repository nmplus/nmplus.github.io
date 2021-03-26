# JDK & maven 설정
  
1. Jenkins 환경 설정  
   외부 접속 URL 설정.  
   GitHub을 사용할 경우, webhook으로 GtiHub에서 접근할 수 있어야 함으로,  
   꼭 외부 IP가 있어야 한다.   

  
![download](https://user-images.githubusercontent.com/24904435/112590780-baeed000-8e46-11eb-94c9-d21840d8b1cb.png)  
  
![download](https://user-images.githubusercontent.com/24904435/112590879-dc4fbc00-8e46-11eb-9454-e846ba269b18.png)
  
2. Global Tool Configuration 메뉴 접근  
  
![download](https://user-images.githubusercontent.com/24904435/112591278-7b74b380-8e47-11eb-907b-c052e7688162.png)  
  
3. Add JDK 클릭  
  
![download](https://user-images.githubusercontent.com/24904435/112591395-a2cb8080-8e47-11eb-9563-cd607964bbd6.png)  
  
4. add JDK를 클릭 시 화면  
  
![download](https://user-images.githubusercontent.com/24904435/112591489-c55d9980-8e47-11eb-9bf3-46c51c766279.png)  
  
5.  JAVA_HOME 부분에 해당 설치 경로 입력.  
    당연하겠지만, 자신의 로컬 컴퓨터 경로 입력 시 에러. 젠킨스가 설치된 서버의 JDK 경로 입력.  
  
![download](https://user-images.githubusercontent.com/24904435/112591678-0eade900-8e48-11eb-9b0e-b29156f3b3c8.png)  
  
![download](https://user-images.githubusercontent.com/24904435/112591767-3735e300-8e48-11eb-9b9a-9c7c3ec7a1cc.png)  
  
6. 조금 더 밑에 있는 Maven 설정도 추가.  
   JDK 설정과 동일하다.  
![download](https://user-images.githubusercontent.com/24904435/112591869-592f6580-8e48-11eb-833e-09e18d8c069b.png)  
  
   
