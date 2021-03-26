# Oracle DB 생성 (1)

오라클 서버를 새로 설치. 다만, 기존에 타버젼(하위버젼)이 설치된 것이 있음.  <br><br>


1. 설치 파일들은 폴더 경로에 영문만 있도록 한다. <br>
   오래 된 에러 사항이었는데, 요즘 버전은 어떤지 확인하지는 않았음. <br><br>

2. 프로그램 실행 이후 첫 화면. <br>
   그냥 다음.  보안갱신 수신도… local이면 없애도 될 듯.  <br>
   ![oracle1](https://user-images.githubusercontent.com/39476251/112245356-1036b000-8c94-11eb-8256-4f6f1fcd4755.JPG)<br><br>

3. 데이터 베이스 생성 선택<br>
   ![oracle2](https://user-images.githubusercontent.com/39476251/112245425-32c8c900-8c94-11eb-95fa-3be8e68a2fc5.JPG)<br><br>
   
4. 서버 클래스는 실운영서버 등에서 사용. <br>
Local 또는 개발장비에서는 데스크톱 클래스를 선택한다. <br>
서버 클래스에서는 좀 더 상세하게 설정하여 설치 할 수 있다. <br>
서버 클래스를 선택하면 이후 화면들이 상세 설정화면들로 변경된다.<br>
![oracle3](https://user-images.githubusercontent.com/39476251/112245705-bd112d00-8c94-11eb-8bfb-85179c21c4ce.JPG)<br><br>

5. 관리자 계정이 아닌 Oracle Home 프로그램의 계정 설정.  <br>
- 기존 Windows 사용자 사용 : 해당 PC 로그인 계정을 그대로 사용. 만약 입력한 계정이 관리자 권한을 가지고 있다면 불가. <br>
- 새 Windows 사용자 생성 :  <br>
- Windows 내장 계정 사용 :  <br>
- ![oracle4](https://user-images.githubusercontent.com/39476251/112245784-e631bd80-8c94-11eb-9954-9724dbefd147.JPG)<br><br>

6. 경로 및 데이터베이스 설정 <br>
전역 데이터베이스 명에는 특수문자 사용이 불가. ( 이미지의 _는 오류로 사용 불가 ) <br>
문자 집합은 UTF8로 설정.  <br>
-> 이것이 DB UTF8로 설정하는 것이 맞는지는 좀 더 확인 필요. <br>
![oracle5](https://user-images.githubusercontent.com/39476251/112245830-02cdf580-8c95-11eb-943b-a6461636d35f.JPG)<br><br>

7. 선택 한 내용들 확인 진행 <br>
 ![oracle6](https://user-images.githubusercontent.com/39476251/112246168-91db0d80-8c95-11eb-8c01-46928aa17409.JPG)<br><br>

8. 설치 전 확인을 위한 Summary <br>
 ![oracle7](https://user-images.githubusercontent.com/39476251/112246253-b3d49000-8c95-11eb-8e6f-a570a174f853.JPG)<br><br>
 
9. 설치 진행 <br>
![oracle8](https://user-images.githubusercontent.com/39476251/112246538-31989b80-8c96-11eb-8c7e-93b39dfd6f01.JPG)<br>
![oracle9](https://user-images.githubusercontent.com/39476251/112246582-437a3e80-8c96-11eb-9012-c635a11ce9f9.JPG)<br><br>

10. 완료 내용 표시  <br>
비밀번호를 각각 설정하고 싶을 경우, 비밀번호 관리를 클릭하여 변경.  <br>
![oracle10](https://user-images.githubusercontent.com/39476251/112246693-5f7de000-8c96-11eb-9e28-8effc9870d83.JPG)<br><br>

11. 완료<br>
![oracle11](https://user-images.githubusercontent.com/39476251/112246748-77edfa80-8c96-11eb-9e80-805eae778c2f.JPG)
