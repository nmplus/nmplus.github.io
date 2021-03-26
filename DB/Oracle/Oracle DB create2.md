# Oracle DB 생성 (2)

오라클 서버 설치 시 DB를 생성하지 않거나, Default는 생성하였으나, 그를 이용하지 못 할 경우 등등에 의해 DB를 새로 생성해야 할 경우. <br><br>

1. 프로그램 실행<br>
![oracle-1](https://user-images.githubusercontent.com/39476251/112246952-d31fed00-8c96-11eb-8f67-595742739b5e.JPG)<br><br>

2. 데이터베이스 생성 선택<br>
![oracle-2](https://user-images.githubusercontent.com/39476251/112247075-fc407d80-8c96-11eb-846c-13eaff166fd6.JPG)<br><br>

3. 범용 또는 트랜잭션 처리 템플릿 선택<br>
![oracle-3](https://user-images.githubusercontent.com/39476251/112247208-445fa000-8c97-11eb-84d9-c50ca3d387d0.JPG)<br>
데이터 웨어하우스 :  <br>
사용자 정의 데이터베이스 : <br><br>

4. 전역 데이터베이스 이름을 적어준다.  <br>
해당 이름과 동일하게 SID가 자동 입력된다.   <br>
다르게 하고 싶다면 SID를 직접 변경해 준다.  <br>
![oracle-4](https://user-images.githubusercontent.com/39476251/112247286-622d0500-8c97-11eb-966d-75091cb949b6.JPG)<br>
전역 데이터베이스 명칭과 SID에 대한 각각의 사용법은? <br>
url="jdbc:oracle:thin:@  :  :dbY2G"  <br>
name="dbY2GS" <br><br>

5. 관리 옵션. 기본 설정 그대로 다음.<br>
 ![oracle-5](https://user-images.githubusercontent.com/39476251/112247382-8983d200-8c97-11eb-8cd5-00b520ec1405.JPG)<br><br>

6.비밀번호 입력  <br>
각 계정에 대해 각기 비밀번호를 입력하거나, 동일한 관리 비밀번호를 입력 <br>
만약 입력한 비밀번호가 오라클에서 권장하는 비밀번호 규칙에 부합하지 않는 경우, 확인창이 팝업. <br>
'예'를 선택하면, 무시하고 그대로 사용할 수 있음.<br>
![oracle-6](https://user-images.githubusercontent.com/39476251/112247447-aa4c2780-8c97-11eb-86cd-e72dd129acc3.JPG)<br><br>

7. 데이터베이스 파일위치 설정.  <br>
기본 설정 이용.  <br>
![oracle-7](https://user-images.githubusercontent.com/39476251/112247518-c780f600-8c97-11eb-8606-8c4acb9fc18f.JPG)<br><br>

8. 복구 구성. 기본 설정으로 다음. <br>
![oracle-9](https://user-images.githubusercontent.com/39476251/112247584-e5e6f180-8c97-11eb-9008-ec7d4d75cbec.JPG)<br><br>

9. 샘플 스키마, 혹은 생성 후 실행 할 스크립트를 정의. <br>
![oracle-8](https://user-images.githubusercontent.com/39476251/112247639-0020cf80-8c98-11eb-896a-37b79d16951b.JPG)<br><br>

10. 초기화 매개변수를 설정한다. <br>
캐릭터셋은 UTF-8로 설정 해 준다.; ( AL32UTF8 ) <br>
DB를 EUC-KR로 설계 할 경우에는 그에 따라 변경이 불필요하다. ( 여러 언어 지원을 위해, UTF-8을 대개 사용 ) <br>
![oracle-10](https://user-images.githubusercontent.com/39476251/112247734-2ba3ba00-8c98-11eb-91e7-76c381b8b2d9.JPG)<br><br>

11. 데이터베이스 저장 영역 설정. 기본 설정으로 셋팅. <br>
![oracle-11](https://user-images.githubusercontent.com/39476251/112247826-4e35d300-8c98-11eb-8edb-82943be92ac5.JPG)<br><br>

12. 생성옵션. 스크립트 등이 있을 경우 선택. 이후 완료. <br>
![oracle-12](https://user-images.githubusercontent.com/39476251/112247912-6a397480-8c98-11eb-9fce-420b115bc652.JPG)<br>
확인 시, 지금까지의 설정 정보를 표시하는 팝업창이 표출되고, <br>
해당 팝업창에서 '확인' 클릭 시 DB생성. <br>
![oracle-13](https://user-images.githubusercontent.com/39476251/112247980-86d5ac80-8c98-11eb-858b-40f939e4ad4f.JPG)
