# EL (Expression Language)

■ EL (Expression Language) 

 

 

사용목적 <%= %>, out.println()과 같은 자바코드를 더 이상 사용하지 않고 좀더 간편하게  

        출력을 지원하기 위한 도구. 

        배열이나 컬렉션에서도 사용되고, JavaBean의 프로퍼티에서도 사용된다. 

        표현식 언어.  

 

문법  Attribute형식에서는 <%= cnt + 1 %>를 쓰지 않고 ${cnt + 1}로 쓰고 

         Parameter형식에서는 ${param.abc}으로 쓴다. 

 

  여기서 cnt는 자바에서는 변수 이름이고, EL 식에서는 Attribute의 이름으로 

         해석되고, 값을 찾을때 Attribute는 작은 Scope에서 큰 Scope로 찾음. 

         (page → request → session → application) 

 

내장객체 1) pageScope → 페이지Scope에 접근 

              2) request Scope → 리퀘스트Scope에 접근 

              3) sessionScope → 세션Scope에 접근 

              4) applicationScope → 어플리케이션Scope에 접근 

              5) param → 파라미터값 얻어올때 ( 1개의 Key에 1개의 Value ) 

              6) paramValues → 파라미터값 배열로 얻어올때( 1개의 Key에 여러개의 Value)  

              7) header → 헤더값 얻어올때 ( 1개의 Key에 1개의 Value )  

              8) headerValues → 헤더값 배열로 얻어올때 ( 1개의 Key에 여러개의 Value )  

              9) cookie → ${cookie. key값. value값}으로 쿠키값 조회 

       10) initParam → 초기 파라미터 조회 

       11) pageContext → 페이지컨텍스트 객체를 참조할때 

 
 

 

 
■ JSTL (Jsp Standard Tag Library) 

 

 

http://archive.apache.org/dist/jakarta/taglibs/standard/binaries/ 

에서 다운로드. Standard.jar와 jstl.jar 파일 프로젝트에 추가, 

 

JSP 제일 상단에 <%@ taglib prefix="c" url="http://java.sun.com/jsp/jstl/core"%> 추가 

 

 

JSTL은? <jsp:include>나 <jsp:usebean>과 같은 커스텀 태그처럼 연산이나 조건문이나 반복문인 

             if문, for문, DB를 편하게 처리할 수 있는것이 JSTL 

 ![el1](https://user-images.githubusercontent.com/58843821/112084804-c767f400-8bcc-11eb-9063-b9d2893fe585.png)
 
 ![el2](https://user-images.githubusercontent.com/58843821/112084802-c6cf5d80-8bcc-11eb-894b-287e7616a4b5.png)
 
 ![el3](https://user-images.githubusercontent.com/58843821/112084818-c931b780-8bcc-11eb-934e-aac11e9bf129.png)
 
 ![el4](https://user-images.githubusercontent.com/58843821/112084814-c931b780-8bcc-11eb-9ef2-b50d71e37037.png)
 
 ![el5](https://user-images.githubusercontent.com/58843821/112084812-c8992100-8bcc-11eb-9807-7e2db6d56446.png)

 ![el6](https://user-images.githubusercontent.com/58843821/112084808-c8992100-8bcc-11eb-84e9-d176d9348293.png)

 

날짜 format 

<fmt:parseDate value='${ vo.regDate }' var='regDate' pattern="yyyy-MM-dd H:m" /> 

<td><fmt:formatDate value="${ regDate }" pattern="MM월dd일 H:m"/></td> 

 

 

split 

문자열을 구분자에 따라 배열로 만드는 함수입니다. 

예를들어 핸드폰번호 010-1111-1111 이라는 문자열이 있을 때 " - "를 기준으로 나누고 싶을 때 사용합니다. 

 

<c:set var="phone" value="${ fn:split(userVO.phone , '-') }" /> 

 

 

합계 

<c:set var ="total" value = "0" /> 

<c:forEach var="price" items="${prices}"> 

        <c:set var= "total" value="${ total + price }"/> 

</c:forEach> 

<c:out value="${total}"/> 

 ![el7](https://user-images.githubusercontent.com/58843821/112084806-c8008a80-8bcc-11eb-8024-2bde3fbff2ff.png)

