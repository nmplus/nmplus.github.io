# 확인해봐야 할 것

1.Tool을 이용하면 괜찮은데, sqlplus로 접속한 상태로, 한글을 입력하려 하면 한글이 모두 깨짐. <br>

2.select * from nls_database_parameters where parameter = 'NLS_CHARACTERSET'; <br>
해 보면 UTF-8이지만, NLS_LANGUAGE가 'AMERICAN' 이다. <br>

3.export NLS_LANG=KOREAN_KOREA.AL32UTF8 ( 리눅스 쉘에서. 윈도우는 미확인 )  <br>
명령어를 이용하여, NLS_LANG을 바꿔주면 괜찮다고 함. -> 테스트를 통한 확인은 아직> <br>
또한, 이미 데이터가 있는 경우, 데이터들 한글이 모두 깨진다고 함. <br>

![checkpoint](https://user-images.githubusercontent.com/39476251/112589151-f50aa280-8e43-11eb-92fc-e3e69a747d11.JPG)
