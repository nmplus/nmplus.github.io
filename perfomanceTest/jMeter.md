# 제이미터(JMeter)

1. JMeter란 ? 

      Apache JMeter는 웹 애플리케이션처럼 클라이언트-서버 구조로 된 소프트웨어의 성능 테스트를 위해서 만들어진 100% 순수 자바 프로그램. 단위/성능/스트레스 테스트 등 많은 곳에서 활용이 가능하며, 프로토콜(Protocol)도 계속 추가되어 TCP, HTTP(S), FTP, JDBC, LDAP, SMTP, SAP/XML, RPC 등 현재 범용으로 사용되는 프로토콜 대부분을 지원. 

      통신 프로토콜 단계에서만 동작하고 웹 브라우저에서는 동작하지 않음. 즉, 통신규약에 맞도록 클라이언트와 서버 간 메시지만 송수신할 뿐이고 클라이언트 자체에서 행해지는 연산 동작은 하지 않음. 가장 대표적인 예가 ActiveX를 이용하여 암호화나 연산 작업을 하는 사이트. 이러한 사이트는 ActiveX 로직을 모두 이해하고 자바를 이용하여 별도로 JMeter 내부 모듈을 구현하지 않는 이상 테스트 불가 

 

 

2. 성능테스트 

      * Load 테스트 : 시스템의 성능을 벤치마크하기 위한 테스트. 이 테스트는 부하(Load)를 순차적으로 증가시키면서 응답시간이 급격히 증가하거나 더는 처리량이 증가하지 않거나 시스템의 CPU와 Memory 등이 기준값 이상으로 증가하는 등 비정상 상태가 발생하는 임계점을 찾아내고 이를 바탕으로 성능 이슈에 대한 튜닝과 테스트를 반복 
      
      * Stress 테스트 : 임계값 이상의 요청이나 비정상적인 요청을 보내 비정상적인 상황의 처리 상태를 확인하고 시스템의 최고 성능 한계를 측정하기 위한 테스트 

      * Spike 테스트 : 예를 들어 빌딩에 화재 경보가 발생했을 때 빌딩에 있는 직원들이 동시에 안전한 장소를 향해서 이동할 경우 시간이 얼마나 걸리며 어떤 문제가 발생하는지를 테스트. 즉, 갑자기 사용자가 몰렸을 때 요청이 정상적으로 처리되는지 그리고 그 업무 부하(Workload)가 줄어들때 정상적으로 반응하는지를 확인하기 위한 테스트 

      * Stability 테스트 / Soak 테스트 : 긴 시간 동안 테스트를 진행해서 테스트 시간에 따른 시스템의 메모리 증가, 성능 정보의 변화 등을 확인하는 테스트를 의미. 짧게는 한두 시간부터 길게는 며칠동안 진행 

      * 테스트 프로세스 : 요구사항 분석 -> 테스트 계획 -> 테스트환경구축 -> 테스트설계 -> 테스트 수행 및 결과 수집 -> 테스트 분석 -> 문제점 수정 및 재테스트 -> 결과 리포트 작성 

 

 

3. 주요용어 

      * Active User : 실제 서버에 연결된 상태로 요청을 처리 중인 사용자 

      * InActive User : 웹브라우저에 결과 화면이 출력된 상태에서 화면의 내용을 읽거나 정보를 입력하고 있는 사용자. 서버와의 세션(Session) 정보를 가지고 있지만 직접 접속하여 요청을 주고받는 상태가 아닌 사용자를 의미 

      * Concurrent User(Active User + InActive User) : 보통 '동시 접속 사용자수'라고 표현. 일반적으로 사용자 수의 많고 적음을 표현하는 값으로, 성능 테스트에서 가상 사용자 수를 결정하는 기준. 서비스 유형과 시간에 따라 그 비율이 달라지긴 하지만, 일반적으로 Active User와 InActive User 비율이 1:10 정도임 

      * Virtual User : 가상 사용자 수로, JMeter에서는 Thread 수로 표현하기도 함 

      * Ramp-up Period : Thread(Virtual User) 생성에 걸리는 시간을 의미. 그래프로 표현한다면 Thread 수 = 10개 / Ramp-Up Period = 50초. '10개의 Thread를 50초 동안 차례대로 생성하라'는 의미이며 5초(50초/10개)마다 Thread를 하나씩 생성하는 것과 같음 

      * Throughput : 단위 시간당 대상 서버(웹서버, WAS, DB 등)에서 처리되는 요청의 수. JMeter에서는 시간단위를 보통 TPS(Transaction Per Second)로 표현 

      * Response Time / Load Time : 응답시간 또는 처리시간이라고 표현. 요청을 보낸 후 응답이 완료되어 사용자 화면에 출력될때까지의 시간을 나타냄. 시스템의 성능을 평가하는 지표로 주로 사용 

      * Latency  : 요청을 보낸 후 데이터를 받기 시작할 때까지 시간 

      * Think Time : 하나의 요청에 응답을 수신하고 다음 요청을 보낼 때까지 시간. 테스트에서 실제 사용자의 사용패턴과 유사한 패턴을 구현하기 위해서는 이 Think Time을 적절히 적용해야 함 

      * Request Interval Time : 요청을 보낸 후 다음 요청을 보낼때까지 시간 

 

4. 제이미터 설치 

      https://jmeter.apache.org/download_jmeter.cgi\ 

      에서 Binaries에 zip파일 설치 후 압축 해제 

      /bin/jmeter.bat 실행 

 

 

5. 사용법 

      1) Thread Group 설정 - 초당 동시 접속자 수 및 요청 횟수 설정 

          TestPlan 우클릭 -> Add -> Threads(Users) -> Thread Group 클릭 

          * number of Threads(user) : 동시 접속자 수 

          * Ramp-Up Period(in seconds) : 1초마다 실행 

          * Loop Count : 실행 횟수 (Forever는 무한) 

      2) HTTP Request 설정 

          Thread Group 우클릭 -> Add -> sampler -> HTTP Request 클릭 

          * Web Server, HTTP Request 입력 

      -------성능테스트 셋팅 완료 

      3) View Results Tree - 요청한 Request, Response의 결과 확인 

                  TestPlan 우클릭 -> Add -> Listner -> View Results Tree 클릭 

      4) Summary Report 

          TestPlan 우클릭 -> Add -> Listener -> Summary Report 클릭 

          * Samples - 서버에 요청한 횟수 

          * Average - 평균 응답 시간(ms) 

          * Min/Max - 최소/최대 응답시간(ms) 

          * Error - 에러율 

          * Throughput - 초당 처리 가능한 요청 횟수 

 

 

* 중간중간.. 배운것들.. 

User Defined Variables : 전역변수 선언 

Host나 loginId, port번호 등등 

 

Debug PostProcessor : 디버그용 

Run했을 때 view Results Tree에서 response 데이터를 자세히 볼 수 있음 

 

JSON Extractor : 변수선언 

 Names of created variables : 사용할 변수명 (basicAdId) 

JSON Path expressions : 변수값 ($.SERVER_RESULT.adId -> response SERVER_RESULT에 들어있는 adId의 값을 가져옴)  

 

http://jsonpath.herokuapp.com/ 

Response 값들 넣고 하단에 JSON Path expression 입력 하면 오른쪽에 값나옴 

 

$..[?(@.mediaName =~ /.*헬로비전.*/i)]$..[?(@.mediaId =~ /.*aaaa.*/i)] 

-> mediaName에 헬로비전이 들어가고 mediaId가 aaaa이 들어가는 값 가져오기 

 

 

 

Loop Controller : 반복되는 구간 
  - Name : Loop controller 이름 
  - Loop Count : 몇번 반복할건지 

 

HTTP Request밑에 JRS223 PreProcessor 파일 추가 

function fn_increseNum(varName){ 

    var loopindex = Number(vars.get("__jm__prdBasicLpCnt__idx"))+1;   -> __jm__Loop controller이름__idx -> 0번째부터 가져옴 

    return vars.get(varName+"s_"+loopindex); 

}; 

  

vars.put("prdBasicId",       fn_increseNum("prdBasicId"));  -> prdBasicId 변수에 fn_increseNum 함수에서 가져온 1번부터 5번까지 값 들어감 

vars.put("prdBasicNm",       fn_increseNum("prdBasicNm")); 

vars.put("prdRatingUnit",   fn_increseNum("prdRatingUnit")); 

vars.put("prdAdType",       fn_increseNum("prdAdType")); 

 

https://jmeter.apache.org/usermanual/functions.html#__groovy 

${__groovy(vars.get("myVar").substring(0\,2))} 

: myVars 변수 가져와서 substring 사용 

https://jmeter-plugins.org/wiki/Functions/#strLensupfont-color-gray-size-1-since-0-4-2-font-sup 

${__substring(test string, 5, 8)}외에 strLen 등 사용하려면 플러그인 설치(Custom JMeter Functions) 

 

 

예제 ) 

랜덤 숫자 가져와서 짝수면 uplus, 홀수면 hellovision 갯수만큼 loopcount 돌리기 (랜덤 숫자 변수 testRandom) 

상품 리스트 > JRS223 PostProcessor 

    var uplusCnt = Number(vars.get("uplusId_matchNr")); 

    var helloCnt = Number(vars.get("hellovisionId_matchNr")); 

    var temp; 

    var index = 1;  

 

    if(${testRandom}%2 == 0) { 

        for(var i=0; i<uplusCnt; i++) { 

            temp = JSON.parse(vars.get("uplusId_"+(i+1))); 

            log.info("uplusId_+++++++++"+vars.get("uplusId_"+(i+1))); 

            log.info("index+++++++++++++++++++"+index+", prdBasicLpCnt_=" + vars.get("uplusId_"+(i+1))); 

            vars.put("prdBasicLpCnt_"+index , vars.get("uplusId_"+(i+1)) ); 

            ++index; 

        } 

    } else { 

        for(var i=0; i<helloCnt; i++) { 

            temp = JSON.parse(vars.get("hellovisionId_"+(i+1))); 

            log.info("hellovisionId_++++++++++++++++++"+vars.get("hellovisionId_"+(i+1))); 

            log.info("prdBasicLpCnt_" + index + vars.get("hellovisionId_"+(i+1))); 

            vars.put("prdBasicLpCnt_"+index , vars.get("hellovisionId_"+(i+1)) ); 

            ++index; 

        } 

    } 

    log.info("outIndex@@@@@@@@@@@@@"+(index-1)); 

    vars.put("indexCnt", (index-1)); 

     

Loop Controller의 Loop Count는 ${indexCnt}로 설정. 

Loop Controller 안에는 상품 등록하는 HTTP Reqeust 

상품 등록 JSR223 Preprocessor 

function fn_increseNum(varName){ 

    var loopindex = Number(vars.get("__jm__prdBasicLpCnt__idx"))+1; 

    var prdBasicInfo = JSON.parse(vars.get("prdBasicLpCnt_"+loopindex)); 

    return prdBasicInfo[varName]; 

    //return vars.get(varName+"s_"+loopindex); 

}; 

  

vars.put("prdBasicId",         fn_increseNum("productBasicId")); 

vars.put("prdBasicNm",         fn_increseNum("productBasicName")); 

vars.put("prdRatingUnit",     fn_increseNum("ratingUnit")); 

vars.put("prdAdType",         fn_increseNum("adType")); 
