---
sort: 5
---
## Spring Security 구현중 오류사례

#### LoginFailHandler 구현시 
- AuthenticationFailureHandler을 상속받아서 Exception이 발생했을시 해당하는 내용을 Front로 전달하고자 할경우 request에 담아서 foward해서 로그인 페이지로 전달할수가 있다.

```
 request.setAttribute("loginFailMsg", "아이디 또는 비밀번호가 틀립니다.");
 request.getRequestDispatcher("/user/loginView").forward(request, response);
```

/user/loginView URL 프로토콜 method를 GetMapping로 제한 해버리게 되면 아래와 같은 오류가 발생 할수 있다.

<strong>
org.springframework.web.HttpRequestMethodNotSupportedException: Request method 'POST' not supported
</strong>

- 호출 url에 RequestMapping을 사용하게되면 GET,POST등 모두 사용가능.
```
...
    @RequestMapping("/user/loginView")
    public String login() {
        return "user/login";
    }

```
