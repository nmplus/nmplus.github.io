# Window에서 사용중인 port 확인 및 kill

- local에서 개발중 Tomcat등 서버를 올릴경우 port 충돌이 발생하는 경우가 있다.  
이전에 실행했던 서버가 background로 점유하고 있는 경우가 대부분이다.  
보통 작업관리자에서 찾아내서 작업종료 하는데 작업관리자는 실제 사용하는 port는 알수없다.

- cmd에서 대상port kill하기

```
#사용중인 port 조회
netstat -a -o -n


  프로토콜  로컬 주소            외부 주소              상태            PID

...중략

  TCP    0.0.0.0:5040           0.0.0.0:0              LISTENING       8200
  TCP    0.0.0.0:7680           0.0.0.0:0              LISTENING       3140
  TCP    0.0.0.0:8080           0.0.0.0:0              LISTENING       1808
  TCP    0.0.0.0:14430          0.0.0.0:0              LISTENING       8632
...

# 해당하는 port의 PID를 찾아 아래명령어 수행
taskkill /F /PID 1808
```
