# Jekyll 블로그 Local에서 실행

## Jekyll 서버 실행
TERMINAL 창에서 아래 명령어 입력 
```
jekyll serve
```
![runJekyllServer1](https://user-images.githubusercontent.com/39661858/110881235-58181780-8323-11eb-9cb1-c3d561e68b2d.png)
버전 에러가 발생한다면 bundle exec 작성해야 한다.

```
bundle exec jekyll serve
```
![runJekyllServer2](https://user-images.githubusercontent.com/39661858/110284110-a0ce8880-8024-11eb-9a5e-7d0e8b3645e4.png)

## 실시간으로 서버 반영
```
bundle exec jekyll serve -w
```
-w : 파일이 수정되었을 때 사이트를 자동으로 다시 생성한다.

## 실행
- [http://127.0.0.1:4000/](http://127.0.0.1:4000/) 확인 가능
- [http://localhost:4000/](http://localhost:4000/) 확인 가능 
![localhost4000](https://user-images.githubusercontent.com/39661858/110284222-ce1b3680-8024-11eb-9767-85e5ce785e88.png)

## Server stop
```
ctrl + c
```