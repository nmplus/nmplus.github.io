# SK 셋팅
  
1. 모든 설정은 jeus 계정으로 설정되어 있습니다.  
   jenkins 기동은 {jeus계정home}/jenkins 폴더의 runJenkins.sh를 실행합니다.  
   백그라운드 프로세스로 실행되도록 되어 있으며, log 파일을 생성하지 않도록 해 두었습니다.  
   만약, 필요하다면 해당 sh 안에 실행명령을 변경하면 됩니다.  
   백그라운드 프로세스이므로, 프로세스 정지는 직접 kill 명령어를 이용합니다.  
![download](https://user-images.githubusercontent.com/24904435/112599530-669e1d00-8e53-11eb-8999-e947e0a7cc3f.png)   
 
2. 소스를 다운로드 받은 SVN 설정 부분입니다.  
![download](https://user-images.githubusercontent.com/24904435/112599649-93eacb00-8e53-11eb-9ecc-51209f213cd3.png)  
  
3. 빌드를 언제할 것인지, 언제 자동으로 할 것인지 설정하는 부분입니다.  
   이 때는 cron 형식으로 특정 시간에 빌드되도록 설정했으나,  
   한수석님과의 통화 이후, 빌드 유발 항목은 모든 설정을 없앴습니다.  
![download](https://user-images.githubusercontent.com/24904435/112599733-aa912200-8e53-11eb-9aef-3a7dc1d8acc2.png)  
  
4. 빌드 환경 설정 부분에서는 빌드 전에 기존 빌드 파일을 모두 삭제하도록 설정합니다.  
![download](https://user-images.githubusercontent.com/24904435/112599957-eb893680-8e53-11eb-92eb-dfad15340bf4.png)  
  
5. 빌드 전 실행해야 할 것이 있을 경우 설정하는 부분입니다.  
   web일 경우의 pom.xml 과 admin 일 경우의 pom.xml의 내용이 다릅니다.  
   module 설정 부분이 다릅니다. 그렇기에, 각 설정 파일을 따로 둔 후,   
   빌드 전에 해당 폴더에 복사하도록 설정합니다.  
  ![download](https://user-images.githubusercontent.com/24904435/112600077-0f4c7c80-8e54-11eb-9663-4d48dad52969.png)  
  
6. 빌드 부분입니다.   
   goal은 빌드한 파일은 따로 복사할 것이므로, package까지만 설정합니다.  
   빌드 시, localrepository를 사용해야 하므로, 해당 settings.xml 경로를 설정해 줍니다.
![download](https://user-images.githubusercontent.com/24904435/112600215-3e62ee00-8e54-11eb-9fac-220bd01bc373.png)  
  
7. 빌드 후 설정 부분입니다.  
   먼저, jeus down. 파일 복사.   
   이후, jeus 재기동입니다.  
   현재 사진에는 각각 나눠서 설정했으나, 이 경우, jeus가 이미 stop 되어 있을 경우,   
   해당 스크립트에서 스크립트 실패로 이후 step이 진행되지 않습니다.   
   그래서, 현재 설정은 모두 하나의 shell 설정 안에 해 두었습니다.  
![download](https://user-images.githubusercontent.com/24904435/112600333-681c1500-8e54-11eb-910c-b1f0e986dcd5.png)  
  
8. 마지막 부분의 exit 0 부분은 무조건 스크립트가 실패로 뜨기에 임의로 성공으로 해 두었습니다.  
   사실 이렇게 해 두면 문제가 있으나, jeus 실행 스크립트 자체에서 에러가 있기에,  
   부득이하게 설정한 부분입니다.  
![download](https://user-images.githubusercontent.com/24904435/112600472-97328680-8e54-11eb-96e0-e82b3b3a2b08.png)  
  
