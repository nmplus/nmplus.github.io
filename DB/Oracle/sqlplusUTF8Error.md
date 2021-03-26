# sqlplus로 접속 시 한글이 깨진다면

1. NLS_LANG(언어설정)은 CHARACTER SET(문자설정)이 아님. <br>
Character Set은 DB 테이블에 입력 가능한 언어를 의미하며,  <br>
NLS_LANG은 오라클에서 표시하는 메시지 및 각종 SQL문에 입력가능한 언어를 의미  <br> <br>

2. 또한, sqlplus로 접속 시, 접속하는 컴퓨터(클라이언트)에 의존한다.  <br>
그러므로, 한글이 깨진다면 DB 서버의 NLS_LANG 을 확인하는 것이 아닌,  <br>
접속하는 클라이언트 컴퓨터의 레지스트리의 NLS_LANG을 확인해야 한다.  <br>
한글 windows라면 무조건 KO16KSC5601을 사용하면 됨. --> OS의 LANG도 연관이 있다.   <br>
==> 확인 결과 상관없음.  <br> <br>

3. 최종 결론. 언어셋이 이곳저곳에서 걸리게된다.  <br>
파일을 UTF-8로 작성했다면,  CMD창에서 sqlplus 로 파일 로드  시 한글이 깨짐 -> chcp 65001 를 이용.   <br>
--> cmd창의 언어셋을 변경하게 되면, sqlplus에서는 파일 안의 한글을 제대로 읽어와서 쿼리를 실행하지만,  <br>
     내부에서 한글이 깨짐.  <br>
이리저리 해 본 결과, 현 시스템( win10, NLS_LANG=KOREAN_KOREA.KO16MSWIN949 )  에 파일은 EUC-KR로 작성  <br>
CMD창의 언어셋도 그대로 하게 되면 정상 작동한다.  <br> <br>

참고 : [http://blog.naver.com/PostView.nhn?blogId=cana01&logNo=130084345196](http://blog.naver.com/PostView.nhn?blogId=cana01&logNo=130084345196)<br>
[http://couplewith.tistory.com/entry/%EC%98%A4%EB%9D%BC%ED%81%B4-Charset-%EB%B3%80%EA%B2%BD-%ED%95%B4%EC%95%BC-%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0%EC%99%80-%EB%B0%A9%EB%B2%95](http://couplewith.tistory.com/entry/%EC%98%A4%EB%9D%BC%ED%81%B4-Charset-%EB%B3%80%EA%B2%BD-%ED%95%B4%EC%95%BC-%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0%EC%99%80-%EB%B0%A9%EB%B2%95)<br>
[http://devilstrike-textcube.blogspot.com/2009/11/nlslang-%EB%B0%8F-character-set-%EC%84%A4%EC%A0%95-%EB%B3%80%EA%B2%BD.html](http://devilstrike-textcube.blogspot.com/2009/11/nlslang-%EB%B0%8F-character-set-%EC%84%A4%EC%A0%95-%EB%B3%80%EA%B2%BD.html)<br>

레지스트리 편집 예<br>
![reg](https://user-images.githubusercontent.com/39476251/112592269-128e3b00-8e49-11eb-8490-c7c567f253d7.JPG)
 
