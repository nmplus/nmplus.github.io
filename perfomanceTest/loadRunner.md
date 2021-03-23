#로드러너(LoadRunner)

1. 왜 사용하는지 ? 

      * 성능테스트에서 성능은 시스템의 처리량, 속도, 메모리 사용량 등이 주어진 환경에서 명시된 기능에 대해 정상적으로 수행하는 것을 말함 

       사용자 요청을 처리하기 위해 소요된 응답시간은 클라이언트에서 측정하고, 단위 시간당 시스템에서 처리되고 있는 처리량은 서버에서 측정함.  

       보통 웹기반 시스템에서는 성능 측정의 기준을 TPS(Transaction Per Second - 단위시간당 처리건수)로 함 

      * 목적  

       ① 안정적인 서비스를 위해 안정성 확보 

       ② 다수의 사용자에 의하여 발생할 수 있는 부하에 대한 예방 

       ③ 서버의 최적화를 위해 서버환경 검사 

       ④ 병목 구간을 파악하여 수정 

      * 유형 

       ① 단위테스트 - 단위 별 업무의 최대한의 성능을 측정하는 단계 

       ② 통합테스트 - 목표를 정해놓고 계산된 부하를 발생시켜 측정하는 단계 

       ③ 임계테스트 - 정해놓은 목표없이 도출할 수 있는 최대 성능을 측정하는 단계 

 

 

2. 주요 용어 

      * Concurrent User(동시사용자) - 해당 시스템을 사용하기 위한 사용자로서, Active Users와 Inactive Users로 분류 
        Active Users는 Request를 수행한 후, 응답을 기다리고 있는 사용자이며, Inactive Users는 Request를 수행하지 않고 대기중인 사용자 
        
      * Load(부하) - 사용자들이 테스트하고자 하는 시스템을 단위시간당 몇 건으로 호출하고 있는지에 대한 빈도 

      * Think Time (대기시간) - 사용자가 다음 요청을 전송하기 전까지의 시간 

      * Response Time (응답시간) - 사용자 요청으 처리하는데 소요되는 총 시간 

      * Request Interval (호출간격) - Response Time + Think Time 

      * Throughput (처리량) - 대상 웹 서버가 부하발생 클라이언트에게 송신한 데이타량 

      * Vuser(Virtual user) - 시스템에 부하를 주기 위한 가상 사용자 

      * Transaction (작업단위) - 하나의 작업이 시작하여 완료되는 시점을 하나의 트랜잭션으로 정의 

      * TPS (단위시간당 처리건수) - 단위 시간에 처리 가능한 트랜잭션의 수 (TPS = ConcurrentUser/Request Interval) 

      * Test Script - 시스템의 성능에 대해 확인하기 위해서 레코딩한 소스 

      * Test Scenario - 어떤 방식으로 시스템에 부하를 줄 것인지 정하는 방식 

      * 병목현상 - 부하가 많이 걸려 전체 시스템에 영향을 주는 현상 

 

 

3. 로드러너 성능테스트 방법 

     ① 스크립트 작성 

     ② 시나리오 작성 

     ③ 실행 및 결과분석 

 

 

4. 구성요소 

     * 로드 제네레이터(Load Generator) : 스크립트를 기반으로 응용 프로그램에 부하를 발생시킴 

     * VuGen(Virtual User Generator) : 스크립트를 만들고 편집함 

     * 컨트롤러(Controller) : 로드 제네레이터의 인스턴스를 통제, 실행하고 배열 

     * 에이전트 프로세스(Agent Process) : 컨트롤러와 로드 제네레이터 인스턴스 간의 연결을 관리 

     * 분석(Analysis) : 다양한 로드 제네레이터로부터 로그를 모아서 실행 결과 데이터의 시각화 및 데이터 감시를 위한 보고서 서식을 만듬 

 

 

☆ 스크립트 작성 ☆ 

1.1 스크립트 작성 (Recording) 

  - 스크립트 작성 대상 업무는 테스트용으로 제공되는 Web Tours 응용 프로그램 사용. 

    시작 > HP Software > HP LoadRunner > Samples > Web에서 실행  

  ① 로드러너 Vugen 실행 후 File – New 

  ② Web[HTTP/HTML] 프로토콜 선택 후 Create 

  ③ 레코딩 하고자 하는 웹 페이지 URL을 URL Address에 입력 후 Options 버튼 클릭 

  ④ 좌측에서 Recording을 선택 

      - HTTP/HTML Level을 HTML-based script로 선택 후 HTML_Advanced 버튼 클릭 

      - Script type을 A script containing ~~ 선택 

      - Non HTML-generated elements를 DO not record 선택 후 OK 

  ⑤ 트랜잭션 이름을 만들기 위해 Start Transaction 아이콘 선택 

  ⑥ 이름 입력(예 : 로그인 혹은 예약확인 등 업무단위) 

      - 트랜잭션 잡는 이유 : 대상업무에 대해 시작과 끝을 정의해서 정의된 트랜잭션에 대해 응답시간, 초당 처리건수 등의 결과를 수집하기 위함 

  ⑦ 해당 업무를 한 뒤 End Transaction 아이콘 선택 

 

1.2 스크립트 작성 (Parameterizing) 

  ① Parameter List 아이콘 선택 

  ② New 버튼을 선택해서 파라미터 이름을 넣음 (예 : id) 

  ③ 파일의 테이블을 생성하기 위해 Create Table 버튼 클릭 

  ④ 파라미터 내용 입력 시 Edit with Notepad 선택 

      - 첫번째 행은 변수 이름 (각각의 값은 콤마나 탭, 공백으로 구분 가능) 

      - 두번째 행부터는 변수에 대한 값들로 사용할 데이터 입력 

      (예 : id, pw 

           aaa, 1234 

           bbb, 1234 

           ccc, 1234 ) 

  ⑤ Select Next row 옵션을 변경하여 파라미터 처리 순서를 설정 

      - Sequential : 차례대로 수행됨 

      - Random : 무작위로 수행됨 

      - Unique : 유저별로 유일하게 한 값만 가질 수 있게 수행됨 

  ⑥ Update Value on 옵션을 변경해서 파라미터 변경방법을 설정 

      - Each iteration : Action 구간이 반복될 때 파라미터 변경 

      - Each occurrence : 파라미터를 만날 때마다 변경 

      - Once : 한개만 사용 

  ⑦ New를 눌러 pw 파라미터 선택 

      - File path를 id.dat으로 설정 : id.dat에 있는 데이터 사용 

      - Select column에서는 By name을 선택하고 변수 중 pw를 선택해서 pw변수에 해당하는 데이터 사용 

      - Select next row에서는 Same line as id를 선택해서 변수 id에 있는 데이터가 같은 행에 있는 값을 파라미터 값으로 설정하면 

        로그인 아이디, 패스워드 값이 사용자 마다 매핑되는 값으로 파라미터 처리를 할 수 있게 됨 

  ⑧ 스크립트에서 파라미터 처리하고자 하는 부분(id)을 마우스로 드래그 후 마우스 오른쪽 버튼 

      -> Use Existing Parameter 선택 -> id 선택 

  ⑨ 스크립트에서 파라미터 처리하고자 하는 부분(pw)을 마우스로 드래그 후 마우스 오른쪽 버튼 

      -> Use Existing Parameter 선택 -> pw 선택 

 

1.3 스크립트 작성(Correlation) 

  - Correlation은 다양한 상황에 맞추어 데이터를 변수화하여 스크립트 처리를 원활하게 하도록 하는 용도로 사용. 

    주로 세션id값 같이 동적으로 변하는 값들 때문에 실제 로드러너 수행시 올바르게 처리가 되지 않는 경우에 변수 처리를 하기 위해 많이 사용 

    예약삭제 업무에서 실제 로드러너 스크립트를 돌려 보면 문서가 실제로 삭제되지 않은 것을 볼 수 있는데 이는 예약 삭제 트랜잭션의 호출 함수가 

    스크립트를 작성하였을 당시의 예약이름을 가지고 삭제를 하기 때문에 예약삭제를 하기 위해서는 작성된 예약목록 중 하나가 선택되어 해당 번호        를 받아와야 함. 따라서 이러한 경우에 Correlation을 사용해야 함 

  - 위에서 작성한 로드러너 스크립트를 실제로 돌려보기(Run) 

     ① Edit Runtime Settings 아이콘 선택 

     ② Run 아이콘 클릭 

        - 우측에 Log를 선택 

        - Log 설정 

            : Enable loggin 체크박스 체크 

            : Log options – Always send message 선택 

            : 하단 Extended log 선택 후 하단 체크박스 3개 모두 선택 

     ③ 스크립트 돌린 후 받은 로그를 분석해보면 아래 빨간색 글자로 되어 있는 값이 예약이 추가 될 때마다 생성됨. 예약삭제에서는 이 값을 가지고 

         예약삭제를 하는 것을 알 수 있음. 따라서 예약확인 업무에 있는 이 값을 Correlation 처리 하면 됨. 

         이 때 사용하는 함수가 web_reg_save_param이라는 함수 

         (F1 -> 색인 -> web_reg_save_param -> 항목보기 누르면 자세한 설명을 볼 수 있음) 

  - Correlation 처리하기 

     ① New Step 선택 

     ② Find Function에 web_reg_save_param을 입력 

     ③ 파라미터 이름 입력, Correlation하는 부분의 Left Boundary, Right Boundary를 입력 

 

1.4 스크립트 작성(Verification) 

  - 스크립트가 페이지를 정상적으로 호출하는 지 확인하기 위해서는 검증이 필요. 대부분의 페이지는 페이지에서 Http 에러 코드(4xx, 5xx)가 발생하게      되면 웹 서버에서 미리 만들어 놓은 에러페이지로 리다이렉트 되는 경우가 있기 때문에 페이지에 검증어를 삽입하지 않으면 로드러너에서 정상 트      랜잭션으로 인식됨. 따라서 이 경우에 스크립트에 검증어를 삽입해서 정상로딩여부를 체크해야함 

    ① New Step을 선택 

    ② Add Step 팝업 창이 뜨면 web_reg_find를 입력 

 

 

 
