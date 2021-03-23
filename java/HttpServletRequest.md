HTTP에는 어떠한 유형의 내용이 전송되는지를 의미하는 Content-Type 헤더가 있다. Content-Type은 미디어타입(구: MIME)이라고도 한다. 

서블릿에선 이 헤더의 값이 application/json 혹은 multipart/form-data일 때, 일반적인 경우와 다르게 HTTP 메시지 바디 라인을 직접 읽는 방식을 사용해야만 전송 데이터에 접근할 수 있다. 

이 때 사용되는 API는 ServletRequest.getInputStream(), ServletRequest.getReader()가 있으며, 이런 형태의 전송 데이터를 'payload body' 혹은 'request body post data'라고 한다.

![httpServletRequest1](https://user-images.githubusercontent.com/58843821/112073688-f2941880-8bb7-11eb-8de9-67c67ee752f8.png)
![httpServletRequest2](https://user-images.githubusercontent.com/58843821/112073765-1192aa80-8bb8-11eb-923a-e2b378737fdd.png)
![httpServletRequest3](https://user-images.githubusercontent.com/58843821/112073772-13f50480-8bb8-11eb-9b6a-fcec93d8b7db.png)
