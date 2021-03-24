# Spring Boot

### 게시판 부분의 service와 repository 수정 필요 

1. 스프링 부트 프로젝트 생성  
    File -> New -> Spring Starter Project  
![springBoot1](https://user-images.githubusercontent.com/58843821/112120076-49721000-8c01-11eb-9c99-c03654020f9e.png)
![springBoot2](https://user-images.githubusercontent.com/58843821/112120083-4aa33d00-8c01-11eb-9ef0-8a2d6fed2907.png)

2. Spring Boot Version 설정 : 2.4.2  
    Dependencies 설정
![springBoot3](https://user-images.githubusercontent.com/58843821/112120084-4aa33d00-8c01-11eb-90ab-e9b964e19f9e.png)

3. pom.xml
![springBoot4](https://user-images.githubusercontent.com/58843821/112120086-4b3bd380-8c01-11eb-8272-f50cc7bf0538.png)

4. application.properties 
![springBoot5](https://user-images.githubusercontent.com/58843821/112120087-4bd46a00-8c01-11eb-81b1-2aeeebe2d9a8.png)

5. 첫 화면 index.html  
src/main/resources/templates 첫 화면 페이지 index.html 생성 및 작성 
![springBoot6](https://user-images.githubusercontent.com/58843821/112120089-4bd46a00-8c01-11eb-8ee8-50c29b3cf8fd.png)
![springBoot7](https://user-images.githubusercontent.com/58843821/112120091-4c6d0080-8c01-11eb-9441-979a8053ebc9.png)

6. com.examples.test.controller 패키지 생성 
![springBoot8](https://user-images.githubusercontent.com/58843821/112120093-4c6d0080-8c01-11eb-8ec7-ed68d11064a4.png)

7. HomeController 클래스 생성
![springBoot9](https://user-images.githubusercontent.com/58843821/112120094-4d059700-8c01-11eb-8da4-8e695e0ad342.png)

8. HomeController 에 첫 화면 페이지 작성 
![springBoot10](https://user-images.githubusercontent.com/58843821/112120098-4d059700-8c01-11eb-896d-ee7233c2c5cc.png)

9. 프로젝트 실행 
![springBoot11](https://user-images.githubusercontent.com/58843821/112120100-4d9e2d80-8c01-11eb-9573-adf98f9ed667.png)

10. 정상 실행 
![springBoot12](https://user-images.githubusercontent.com/58843821/112120103-4e36c400-8c01-11eb-9294-8ae7f3777c4d.png)



### 게시판

1. com.example.test.dto 패키지 생성 
![springBoot13](https://user-images.githubusercontent.com/58843821/112120107-4e36c400-8c01-11eb-91c5-1dd1c8382fd6.png)

2. Board 클래스 생성 및 작성 
![springBoot14](https://user-images.githubusercontent.com/58843821/112120108-4ecf5a80-8c01-11eb-88c6-d320dd583cb9.png)
![springBoot15](https://user-images.githubusercontent.com/58843821/112120111-4ecf5a80-8c01-11eb-8d5a-b743bcbfd075.png)

3. src/main/resources/templates 글 작성 페이지 writeBoardForm.html 생성 및 작성 
![springBoot16](https://user-images.githubusercontent.com/58843821/112120113-4f67f100-8c01-11eb-8449-974c4fdab1a2.png)

4. HomeController 에서 글 작성 페이지 작성 
![springBoot17](https://user-images.githubusercontent.com/58843821/112120118-50008780-8c01-11eb-9abb-ff3b4a7f95d9.png)

5. index.html 페이지에 게시판 작성 
![springBoot18](https://user-images.githubusercontent.com/58843821/112120119-50008780-8c01-11eb-8f50-85e9e79e3b5d.png)
![springBoot19](https://user-images.githubusercontent.com/58843821/112120121-50991e00-8c01-11eb-9d89-ea89622803ad.png)

6. 글 작성 실행 화면   
![springBoot20](https://user-images.githubusercontent.com/58843821/112120122-5131b480-8c01-11eb-9020-433d6628bb92.png)

7. writeBoardForm.html 내용 게시글 작성 폼으로 수정 
![springBoot21](https://user-images.githubusercontent.com/58843821/112120123-5131b480-8c01-11eb-8d80-669835595396.png)

8. 게시글 작성 폼
![springBoot22](https://user-images.githubusercontent.com/58843821/112120124-51ca4b00-8c01-11eb-937e-c4c5e803050e.png)

9. 게시글 작성 구현  
com.example.test.repository 패키지 생성 
![springBoot23](https://user-images.githubusercontent.com/58843821/112120127-5262e180-8c01-11eb-812b-c31ed6c5cd25.png)

10. BoardRepository 인터페이스 생성 
![springBoot24](https://user-images.githubusercontent.com/58843821/112120131-5262e180-8c01-11eb-820a-7cb9516d06a3.png)

11. BoardRepository 인터페이스 작성  
JpaRepository 인터페이스 상속 받기  
JpaRepository 에서 기본적인 CRUD 기능 제공해주기 때문에 사용 가능 
![springBoot25](https://user-images.githubusercontent.com/58843821/112120134-52fb7800-8c01-11eb-8b68-e6866d334509.png)

12. HomeContorller 에 글 작성 구현  
글 작성시 게시글 리스트 페이지로 이동하게 수정 
![springBoot26](https://user-images.githubusercontent.com/58843821/112120136-53940e80-8c01-11eb-9c8e-54ad4c987b44.png)
![springBoot27](https://user-images.githubusercontent.com/58843821/112120139-542ca500-8c01-11eb-829d-5cda736fac3e.png)

13. src/main/resources/templates 게시글 리스트 페이지 boardList.html 생성 및 작성 
![springBoot28](https://user-images.githubusercontent.com/58843821/112120141-542ca500-8c01-11eb-9871-41cf7ba4b6d2.png)

    실행  
![springBoot29](https://user-images.githubusercontent.com/58843821/112120143-54c53b80-8c01-11eb-986a-1cc7c44a9236.png)

14. 글 작성 실행  
HomeController
![springBoot30](https://user-images.githubusercontent.com/58843821/112120146-555dd200-8c01-11eb-9fc5-724413bb9446.png)

    writeBoardForm.html
![springBoot31](https://user-images.githubusercontent.com/58843821/112120151-555dd200-8c01-11eb-88ae-a4589e82bde6.png)

    실행 화면   
![springBoot32](https://user-images.githubusercontent.com/58843821/112120153-55f66880-8c01-11eb-944b-18cfc6a86a38.png)
![springBoot33](https://user-images.githubusercontent.com/58843821/112120156-568eff00-8c01-11eb-8191-54395c1a8b59.png)
![springBoot34](https://user-images.githubusercontent.com/58843821/112120158-568eff00-8c01-11eb-9970-430c7e3e47f1.png)

15. 게시글 리스트 구현   
    HomeController 
![springBoot35](https://user-images.githubusercontent.com/58843821/112120162-57279580-8c01-11eb-89e9-2a2c3e4f30a3.png)

    boardList.html 
![springBoot36](https://user-images.githubusercontent.com/58843821/112120165-57279580-8c01-11eb-917d-90e61a700740.png)

    실행 화면 
![springBoot37](https://user-images.githubusercontent.com/58843821/112120167-57c02c00-8c01-11eb-991c-00728010f4ca.png)

16. index.html 에서 게시판 클릭 시 게시글 작성 이 아닌 게시글 리스트로 수정 
![springBoot38](https://user-images.githubusercontent.com/58843821/112120170-5858c280-8c01-11eb-8a51-5061c7fe4500.png)

17. 게시글 리스트에서 게시글 클릭 시 상세보기와 게시글 수정 가능하게 구현 
![springBoot39](https://user-images.githubusercontent.com/58843821/112120174-5858c280-8c01-11eb-8833-f0db94c5d0b7.png)
![springBoot40](https://user-images.githubusercontent.com/58843821/112120179-58f15900-8c01-11eb-8580-2d8a17ca6a26.png)
![springBoot41](https://user-images.githubusercontent.com/58843821/112120183-58f15900-8c01-11eb-88d4-72aaedc02eb9.png)
![springBoot42](https://user-images.githubusercontent.com/58843821/112120186-5989ef80-8c01-11eb-999a-ccdff8cd938e.png)
![springBoot43](https://user-images.githubusercontent.com/58843821/112120191-5a228600-8c01-11eb-8f2c-ec4bddca8ad4.png)  
![springBoot44](https://user-images.githubusercontent.com/58843821/112120192-5a228600-8c01-11eb-8126-2ae7d67c9efd.png)


18. 게시글 삭제 구현 
![springBoot45](https://user-images.githubusercontent.com/58843821/112120194-5abb1c80-8c01-11eb-8c34-32a75d94ea58.png)  
![springBoot46](https://user-images.githubusercontent.com/58843821/112120198-5abb1c80-8c01-11eb-9060-de26e7465297.png)  
![springBoot47](https://user-images.githubusercontent.com/58843821/112120201-5b53b300-8c01-11eb-95b3-20d09b63e492.png)  
![springBoot48](https://user-images.githubusercontent.com/58843821/112120204-5b53b300-8c01-11eb-96b9-7263ccf88ea2.png)
![springBoot49](https://user-images.githubusercontent.com/58843821/112120205-5bec4980-8c01-11eb-89c4-9c3b22e3de83.png)



19. 비밀번호 입력 구현  
    com.example.test.validate 패키지 생성 
![springBoot50](https://user-images.githubusercontent.com/58843821/112120207-5c84e000-8c01-11eb-8c7f-cd37fdceb86a.png)


    
    BoardValidator 클래스 생성 
![springBoot51](https://user-images.githubusercontent.com/58843821/112120210-5c84e000-8c01-11eb-8007-c863a511ec4b.png)


    BoardValidator 클래스 생성 Validator 상속 받고 메소드 오버라이딩 작성
![springBoot52](https://user-images.githubusercontent.com/58843821/112120212-5d1d7680-8c01-11eb-87c4-70026bc21c42.png)



    HomeController 에서 boardValidator 내용 추가 
![springBoot53](https://user-images.githubusercontent.com/58843821/112120213-5db60d00-8c01-11eb-9ec4-b1524eccf121.png)   
![springBoot54](https://user-images.githubusercontent.com/58843821/112120215-5db60d00-8c01-11eb-9fe8-f50ee532aedd.png)
![springBoot55](https://user-images.githubusercontent.com/58843821/112120222-5e4ea380-8c01-11eb-9e39-f3c86898f4e6.png)

20. 조회수 구현  
![springBoot56](https://user-images.githubusercontent.com/58843821/112120225-5e4ea380-8c01-11eb-8dee-2cf8640dc753.png)
![springBoot57](https://user-images.githubusercontent.com/58843821/112120227-5ee73a00-8c01-11eb-83ed-c187dca1ffec.png)
![springBoot58](https://user-images.githubusercontent.com/58843821/112120229-5f7fd080-8c01-11eb-83f3-f49a10bf0288.png)



21. 페이징 구현  
    HomeController
![springBoot59](https://user-images.githubusercontent.com/58843821/112120233-5f7fd080-8c01-11eb-95f0-8d78128a0ac9.png)


    
    boardList.html
![springBoot60](https://user-images.githubusercontent.com/58843821/112120235-60186700-8c01-11eb-9413-dceecdab9f7b.png)
![springBoot61](https://user-images.githubusercontent.com/58843821/112120238-60186700-8c01-11eb-9870-e34bf12948ae.png)
![springBoot62](https://user-images.githubusercontent.com/58843821/112120239-60b0fd80-8c01-11eb-8fb2-eca606fffec9.png)  

 
### Spring Security
1. 회원 디비와 연결할 entity, dto 생성  
    com.example.test.model 패키지 생성 
![springBoot63](https://user-images.githubusercontent.com/58843821/112120240-61499400-8c01-11eb-9d91-afcb2d98971f.png)


    
    MemberEntity 클래스 생성 
![springBoot64](https://user-images.githubusercontent.com/58843821/112120242-61499400-8c01-11eb-8400-be6e5e602cc3.png)


    MemberEntity 클래스 작성
![springBoot65](https://user-images.githubusercontent.com/58843821/112120244-61e22a80-8c01-11eb-873e-c3518d2c25af.png)

    
    com.example.test.dto -> Member 클래스 생성
![springBoot66](https://user-images.githubusercontent.com/58843821/112120245-61e22a80-8c01-11eb-9ea9-825d888127b4.png)

    
    Member 클래스 작성 
![springBoot67](https://user-images.githubusercontent.com/58843821/112120246-627ac100-8c01-11eb-96f3-2bd139b20c2e.png)

    
2. 회원가입 구현  
index.html 에 회원가입 작성  
![springBoot68](https://user-images.githubusercontent.com/58843821/112120249-627ac100-8c01-11eb-8790-06374bc371eb.png)


    src/main/resources/templates 회원가입 페이지 signup.html 생성 및 작성  
![springBoot69](https://user-images.githubusercontent.com/58843821/112120252-63135780-8c01-11eb-9234-50870730f08a.png)

    
    HomeController 에서 회원가입 페이지 나오게 작성
![springBoot70](https://user-images.githubusercontent.com/58843821/112120255-63abee00-8c01-11eb-88ab-55793a7579a2.png)

    
    실행 화면  
![springBoot71](https://user-images.githubusercontent.com/58843821/112120256-63abee00-8c01-11eb-8317-7130fe703b3e.png)

    
    회원가입 클릭 시 회원가입 페이지로 이동 확인  
![springBoot72](https://user-images.githubusercontent.com/58843821/112120258-64448480-8c01-11eb-888d-a7eba2ec82ee.png)

    
    com.example.test.service 패키지 생성  
![springBoot73](https://user-images.githubusercontent.com/58843821/112120259-64448480-8c01-11eb-8351-a0ab241e6a25.png)

    
    MemberService 클래스 생성 및 작성  
![springBoot74](https://user-images.githubusercontent.com/58843821/112120261-64dd1b00-8c01-11eb-9763-d94e2ffa23b0.png)

    
    com.example.test.repository  -> MemberRepository 인터페이스 생성   
![springBoot75](https://user-images.githubusercontent.com/58843821/112120262-6575b180-8c01-11eb-8562-5e766de68a95.png)

    MemberRepository 인터페이스 작성  
![springBoot76](https://user-images.githubusercontent.com/58843821/112120266-6575b180-8c01-11eb-82f0-6f0b6765be90.png)

    HomeController 내용 수정  
![springBoot77](https://user-images.githubusercontent.com/58843821/112120269-660e4800-8c01-11eb-8708-3466267606c4.png)

    
    MemberService 내용 수정
![springBoot78](https://user-images.githubusercontent.com/58843821/112120271-660e4800-8c01-11eb-90bb-48c90eaed129.png)

    
    회원가입 실행화면 
![springBoot79](https://user-images.githubusercontent.com/58843821/112120273-66a6de80-8c01-11eb-8408-002bcba0be69.png)  
![springBoot80](https://user-images.githubusercontent.com/58843821/112120275-673f7500-8c01-11eb-917a-2f9f8a92e95e.png)



    
3. 회원가입 완료 시 로그인 페이지로 이동하게 수정   
    src/main/resrcoues/templates 로그인 페이지 login.html 생성 및 작성  
![springBoot81](https://user-images.githubusercontent.com/58843821/112120278-673f7500-8c01-11eb-9524-e5f1e175e96e.png)

    
    회원 가입 실행
![springBoot82](https://user-images.githubusercontent.com/58843821/112120281-67d80b80-8c01-11eb-970a-3003bae48a41.png)

    
    회원 가입 완료 후 로그인 페이지로 이동 완료
![springBoot83](https://user-images.githubusercontent.com/58843821/112120283-67d80b80-8c01-11eb-98ae-dfe7d082f2fc.png)  
![springBoot84](https://user-images.githubusercontent.com/58843821/112120285-6870a200-8c01-11eb-8184-1aba41604c8f.png)


    
4. 로그인 구현  
    index.html 에 로그인 추가 
![springBoot85](https://user-images.githubusercontent.com/58843821/112120287-6870a200-8c01-11eb-8d0f-36802cbc8a64.png)



    
    HomeController 로그인 시 로그인 성공 페이지로 이동 작성 
![springBoot86](https://user-images.githubusercontent.com/58843821/112120288-69093880-8c01-11eb-8121-008c495e88b6.png)


    
    src/main/resources/templates 로그인 성공 페이지 loginSuccess.html 생성 및 작성 
![springBoot87](https://user-images.githubusercontent.com/58843821/112120290-69a1cf00-8c01-11eb-885f-32a37e186901.png)


    
    로그인 실행화면 
![springBoot88](https://user-images.githubusercontent.com/58843821/112120294-6a3a6580-8c01-11eb-88c8-a59fafd4a5db.png)

    로그인 성공 시 로그인 성공 페이지로 이동 확인 완료 
![springBoot89](https://user-images.githubusercontent.com/58843821/112120296-6a3a6580-8c01-11eb-8060-77f00985f41a.png)

5. 로그아웃 구현  
    index.html 에 로그아웃 추가  
![springBoot90](https://user-images.githubusercontent.com/58843821/112120298-6ad2fc00-8c01-11eb-846a-38044cb0031a.png)


    
    HomeController 에 로그아웃 구현  
![springBoot91](https://user-images.githubusercontent.com/58843821/112120301-6ad2fc00-8c01-11eb-967a-4ac150e2919d.png)


    
    로그아웃 페이지 logout.html 생성 및 작성 
![springBoot92](https://user-images.githubusercontent.com/58843821/112120304-6b6b9280-8c01-11eb-8e1a-fedcfd150ab8.png)


    로그아웃 실행  
![springBoot93](https://user-images.githubusercontent.com/58843821/112120307-6c042900-8c01-11eb-86cf-d72f2a0f8969.png)



6. Spring Security 설정    
    pom.xml  
![springBoot94](https://user-images.githubusercontent.com/58843821/112120308-6c042900-8c01-11eb-8789-d3cae1ae72bb.png)


7. com.example.test.model -> enum -> Role 생성 및 작성  
![springBoot95](https://user-images.githubusercontent.com/58843821/112120311-6c9cbf80-8c01-11eb-919a-b5f1b58ec5dc.png)

8. MemberRepository 수정  
![springBoot96](https://user-images.githubusercontent.com/58843821/112120313-6c9cbf80-8c01-11eb-860f-5d0d9f577bbc.png)

9. MemberService 수정  
![springBoot97](https://user-images.githubusercontent.com/58843821/112120316-6d355600-8c01-11eb-932f-0cc8a49aaffb.png)


10. 스프링 시큐리티 사용 작성  
    com.example.test.config 패키지 생성  
![springBoot98](https://user-images.githubusercontent.com/58843821/112120318-6dcdec80-8c01-11eb-9f2c-4c1e27e92df3.png)

    WebSecurityConfig 클래스 생성 및 작성
![springBoot99](https://user-images.githubusercontent.com/58843821/112120320-6dcdec80-8c01-11eb-87ec-2ff97ee4ecc5.png)


11. HomeController 수정  
![springBoot100](https://user-images.githubusercontent.com/58843821/112120908-06fd0300-8c02-11eb-88ae-6f834a28de8e.png)

12. index.html 수정    
![springBoot101](https://user-images.githubusercontent.com/58843821/112120914-07959980-8c02-11eb-9cb7-c0bda304b708.png)

13. loginSuccess.html 수정  
![springBoot102](https://user-images.githubusercontent.com/58843821/112120916-082e3000-8c02-11eb-8653-53a9c97b3296.png)


14. index.html 에 내정보와 관리자 추가  
![springBoot103](https://user-images.githubusercontent.com/58843821/112120919-082e3000-8c02-11eb-8c4d-d00347730832.png)

15. HomeController 수정  
![springBoot104](https://user-images.githubusercontent.com/58843821/112120921-08c6c680-8c02-11eb-8257-dd102ea64a65.png)

16. myinfo.html 과 admin.html 생성 및 작성  
    내정보 페이지 myinfo.html  
![springBoot105](https://user-images.githubusercontent.com/58843821/112120922-08c6c680-8c02-11eb-93c7-49281dca987d.png)

    관리자 페이지 admin.html 
![springBoot106](https://user-images.githubusercontent.com/58843821/112120924-095f5d00-8c02-11eb-953b-f621c7769ce1.png)

17. 실행  
![springBoot107](https://user-images.githubusercontent.com/58843821/112120929-09f7f380-8c02-11eb-98a8-134611c20f04.png)
![springBoot108](https://user-images.githubusercontent.com/58843821/112120931-09f7f380-8c02-11eb-84b5-6981f9dab4f9.png)
![springBoot109](https://user-images.githubusercontent.com/58843821/112120933-0a908a00-8c02-11eb-8d74-b1b902c67764.png)
![springBoot110](https://user-images.githubusercontent.com/58843821/112120935-0a908a00-8c02-11eb-93a4-eba9c4f6db35.png)
![springBoot111](https://user-images.githubusercontent.com/58843821/112120939-0b292080-8c02-11eb-992a-23c62268e846.png)
![springBoot112](https://user-images.githubusercontent.com/58843821/112120941-0b292080-8c02-11eb-8594-dc4f46e2ca6c.png)
![springBoot113](https://user-images.githubusercontent.com/58843821/112120942-0bc1b700-8c02-11eb-828f-05949b6eeb9a.png)
![springBoot114](https://user-images.githubusercontent.com/58843821/112120943-0bc1b700-8c02-11eb-8f85-35114b561037.png)
![springBoot115](https://user-images.githubusercontent.com/58843821/112120944-0c5a4d80-8c02-11eb-9f55-fd32c39f121c.png)
![springBoot116](https://user-images.githubusercontent.com/58843821/112120945-0c5a4d80-8c02-11eb-83cd-9faa14dd6bed.png)
![springBoot117](https://user-images.githubusercontent.com/58843821/112120947-0cf2e400-8c02-11eb-8517-7519cc5385d1.png)
![springBoot118](https://user-images.githubusercontent.com/58843821/112120949-0d8b7a80-8c02-11eb-8970-c97aa615b875.png)
![springBoot119](https://user-images.githubusercontent.com/58843821/112120950-0d8b7a80-8c02-11eb-9d4e-430a0876285d.png)  
![springBoot120](https://user-images.githubusercontent.com/58843821/112120952-0e241100-8c02-11eb-995d-d01b3d4bcd74.png)  
![springBoot121](https://user-images.githubusercontent.com/58843821/112120953-0ebca780-8c02-11eb-8dcf-e452a09c07ae.png)   
![springBoot122](https://user-images.githubusercontent.com/58843821/112120956-0ebca780-8c02-11eb-8f6a-56d0c58cb5e7.png)  

18. 게시판, 회원 분리하기 (html 폴더, 컨트롤러)
![springBoot123](https://user-images.githubusercontent.com/58843821/112120959-0f553e00-8c02-11eb-843c-5f04cdc3f3f6.png)  
![springBoot124](https://user-images.githubusercontent.com/58843821/112120963-0fedd480-8c02-11eb-851f-8ee399aead8f.png)  
![springBoot125](https://user-images.githubusercontent.com/58843821/112120965-10866b00-8c02-11eb-92da-33821d1a9c9d.png)  
![springBoot126](https://user-images.githubusercontent.com/58843821/112120966-10866b00-8c02-11eb-914d-17d0f090c083.png)  
![springBoot127](https://user-images.githubusercontent.com/58843821/112120969-111f0180-8c02-11eb-9850-53c04e968263.png)
![springBoot128](https://user-images.githubusercontent.com/58843821/112120970-111f0180-8c02-11eb-831c-a52a14bf4e2a.png)  
![springBoot129](https://user-images.githubusercontent.com/58843821/112120972-11b79800-8c02-11eb-803e-687c9ea320e5.png)




### 부트스트랩 적용  
![springBoot130](https://user-images.githubusercontent.com/58843821/112120977-12502e80-8c02-11eb-95a1-ef99cfa4bdf5.png)

index.html  
![springBoot131](https://user-images.githubusercontent.com/58843821/112120980-12502e80-8c02-11eb-9717-14e6688125e7.png)  
![springBoot132](https://user-images.githubusercontent.com/58843821/112120983-12e8c500-8c02-11eb-9c71-05b83b2d1174.png)


index.html 페이지 공통으로 사용되므로 frame 폴더 생성 후 이동  
![springBoot133](https://user-images.githubusercontent.com/58843821/112120985-13815b80-8c02-11eb-9687-0144767a544f.png)  
![springBoot134](https://user-images.githubusercontent.com/58843821/112233655-2afe2a00-8c7e-11eb-83f0-cf2a4624e1ad.png)  
![springBoot135](https://user-images.githubusercontent.com/58843821/112233656-2afe2a00-8c7e-11eb-94e8-34988cbbd882.png)  

공통 사용이므로 이름 common 으로 변경  
![springBoot136](https://user-images.githubusercontent.com/58843821/112233657-2b96c080-8c7e-11eb-9def-a95d7ead0f47.png)  

index.html 파일 생성  
![springBoot137](https://user-images.githubusercontent.com/58843821/112233659-2b96c080-8c7e-11eb-9c12-173c3d421d4f.png)  


index.html 파일 작성  
![springBoot138](https://user-images.githubusercontent.com/58843821/112233660-2c2f5700-8c7e-11eb-9595-f304fe311517.png)
![springBoot139](https://user-images.githubusercontent.com/58843821/112233662-2cc7ed80-8c7e-11eb-9ece-70333fa143e6.png)


부트스트랩 적용하지 않은 원본은 파일명 뒤에 2를 붙임  
![springBoot140](https://user-images.githubusercontent.com/58843821/112233663-2cc7ed80-8c7e-11eb-8a1d-e139e0e8fdd0.png)

회원가입 페이지 signup.html
![springBoot141](https://user-images.githubusercontent.com/58843821/112233666-2d608400-8c7e-11eb-8c00-17a80024afc5.png)  
![springBoot142](https://user-images.githubusercontent.com/58843821/112233668-2d608400-8c7e-11eb-9acc-04325babd62e.png)

로그인 페이지 login.html  
![springBoot143](https://user-images.githubusercontent.com/58843821/112233671-2df91a80-8c7e-11eb-95f3-0c664d918778.png)  
![springBoot144](https://user-images.githubusercontent.com/58843821/112233673-2df91a80-8c7e-11eb-8537-dac0cae25b37.png)
![springBoot145](https://user-images.githubusercontent.com/58843821/112233675-2e91b100-8c7e-11eb-961b-d61233cee690.png)

로그인 성공 페이지 loginSuccess.html
![springBoot146](https://user-images.githubusercontent.com/58843821/112233676-2f2a4780-8c7e-11eb-9f43-beae201bb637.png)
![springBoot147](https://user-images.githubusercontent.com/58843821/112233678-2f2a4780-8c7e-11eb-814b-65b319fbbf24.png)

내정보 페이지 myinfo.html
![springBoot148](https://user-images.githubusercontent.com/58843821/112233680-2fc2de00-8c7e-11eb-91a8-8f7ea51c9dea.png)
![springBoot149](https://user-images.githubusercontent.com/58843821/112233681-2fc2de00-8c7e-11eb-884a-af03c7fcaca2.png)
![springBoot150](https://user-images.githubusercontent.com/58843821/112233683-305b7480-8c7e-11eb-9e05-7fa0d1e38d9e.png)

로그아웃 페이지 logout.html  
![springBoot151](https://user-images.githubusercontent.com/58843821/112233684-305b7480-8c7e-11eb-807d-3dfb1e3123f7.png)
![springBoot152](https://user-images.githubusercontent.com/58843821/112233686-30f40b00-8c7e-11eb-9557-e229af076241.png)

관리자 페이지 admin.html 
![springBoot153](https://user-images.githubusercontent.com/58843821/112233633-26397600-8c7e-11eb-9fe2-ee6f7c475e58.png)
![springBoot154](https://user-images.githubusercontent.com/58843821/112233636-276aa300-8c7e-11eb-956a-ae9b04d9385c.png)
![springBoot155](https://user-images.githubusercontent.com/58843821/112233637-276aa300-8c7e-11eb-8a61-9d8f244ed365.png)

부트스트랩 적용하지 않은 원본은 파일명 뒤에 2를 붙임 
![springBoot156](https://user-images.githubusercontent.com/58843821/112233640-28033980-8c7e-11eb-933e-0d36f71b8dea.png)

게시글 리스트 페이지 boardList.html  
![springBoot157](https://user-images.githubusercontent.com/58843821/112233642-28033980-8c7e-11eb-9c63-8b688e7b46af.png)
![springBoot158](https://user-images.githubusercontent.com/58843821/112233643-289bd000-8c7e-11eb-808d-2830a4c21d08.png)

게시글 작성 페이지 writeBoardForm.html 
![springBoot159](https://user-images.githubusercontent.com/58843821/112233646-29346680-8c7e-11eb-921e-3a06d4d52640.png)
![springBoot160](https://user-images.githubusercontent.com/58843821/112233648-29ccfd00-8c7e-11eb-95da-830c386ecc6e.png)

css  
![springBoot161](https://user-images.githubusercontent.com/58843821/112233651-29ccfd00-8c7e-11eb-9b3d-dea2da9eb156.png)

starter-template.css 
![springBoot162](https://user-images.githubusercontent.com/58843821/112233652-2a659380-8c7e-11eb-9bd1-960c7d0dff69.png)

signin.css  
![springBoot163](https://user-images.githubusercontent.com/58843821/112233654-2a659380-8c7e-11eb-9865-4eb17725d799.png)

