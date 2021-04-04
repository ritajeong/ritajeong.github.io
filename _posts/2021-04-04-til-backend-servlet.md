---
layout: post
title: "이클립스 및 Zulu -sun.security.ssl 관련 오류"
subtitle: ""
categories: til
tags: til
comments: true
date: 2021-04-01 22:45:00 -0400
---

## Web Architecture

### Frontend
- Client : Web browser. (html, javascript, css)
웹브라우저 상에서 이루어지는 모든 입력을 받는다. 
- request : 클라이언트가 서버에게 요청함. 이 때 넘어가는 데이터를 파라미터라고 한다. 
요청이 넘어가면, 실제로 서버에서 어떻게 처리될까?
- response : 서버에서 처리되어서 돌아오는 응답. 

###  Backend
- Web Server : www.naver.com에 접속하면, 내가 접속한 것을 처리할 수 있는 서버가 필요하다. 이것을 웹서버라고 함. httpServer라고도 한다. 
웹서버는 단순히 클라이언트의 접속 처리를 함.  
http Server 는 http 프로토콜을 처리함. 즉, http, css, js만 처리가능하다.  
- Applecations Server : 웹 서버와 데이터베이스 서버를 연결. 
실질적으로 로직처리를 한다. 
일반적인 Business Logic과  DB관련된 Persistence Logic, 그리고 화면에 보이는 역할로서 Presentation의 일처리를 한다.  
여기서 발생하는 응답이 response로서 웹 브라우저에 전달된다. 
- DBMS : 데이터베이스 서버.   

- WAS : 웹 서버와 Application서버를 통합해서 관리함. WebLogic, WebSquere, 제우스, 톰캣 등이 있다.  

- Application Server에서 자바를 사용한다.  
Web에서 수행할 수 있는 자바. 즉, Server Side Server  
보통 사용하는 자바는 Java SE(Standard Edition)기반으로 개발했지만,  
웹 개발을 할 때는 Java EE(Enterprise Edition)을 사용함.  
Java EE에서 화면단에서 처리하는 기술 api인 servlet을 사용함.  
즉, 웹에서 돌아가는 자바를 서블릿이라고 생각하면 된다.  

- JSP : Java Server Page. 문법은 서블릿을 따른다.  


## Servlet
- 서블릿의 목적 : 클라이언트의 요청을 받아서 일처리를 하고 응답함.  

### javax.servlet
javax.servlet 패키지에 가면, Servlet 인터페이스가 있다.  
인터페이스를 implements 하면, 해당 인터페이스가 가지고 있는 추상 메소드를 override해야한다.  

```java
 public class ServletExample implements Servlet{
     //override : init, destroy, getServletConfig, getServletInfo.
 }
```

그래서 Servlet 인터페이스를 implements를 하면 5개의 추상메소드를 override해야하고, 
이들은 destroy와 getServletConfig, getServletInfo, init, service 이렇게 5개의 추상메소드이다. 

### Servlet interface의 5가지 메소드
이 메소드들은 개발자가 호출할 수 있는 메소드가 아니다.  
톰캣이라는 WAS가, 알아서 호출하는 메소드들이다. 
- destroy : servlet이 WAS에서 제거될 때 최종적으로 호출된다. 자동적으로)
- getServletConfig, getServletInfo.
- init : initialize. destroy의 반대작업을 한다. 보통 생성자에서 초기화를 하지만, (Servlet도 생성자가 따로 있다. ) 일반적으로 생성자는 객체를 메모리에 올려주는 역할을 한다. init 메소드는 객체의 초기화 작업을 한다.  
- service : 클라이언트의 요청인 request, service에서 일해서 보낼 응답, 동작인 response를 가지고 메소드 내부에서 요청을 처리한다. 가장 핵심적인, 반드시 만들어야할 메소드이다. 

### Servlet interface를 이미 구현해놓은 클래스
- FacesServlet, GenericServlet, HttpServlet.  
- GenericServlet : abstract 메소드인 service가 존재함.  
```java
public class ServletExample2 extends GenericServlet{
    //override : service메소드 1개만 override한다.
}
```

GenericServlet을 상속받을 때의 단점 : request가 GET인지 POST방식인지 if, else로 각각 구현한다.  

### html의 form 태그에서 데이터 전송
GET, POST 방식이 있다.  
- GET은 url뒤에 query string이 붙어서 전달된다.  
길이제한이 있고, url에 노출된다.  
- POST는 method의 요청페이지의 body에 포함되기 때문에 길이제한, 노출의 위험성이 적다.  
- GET, POST의 데이터 처리방식이 조금 다름.  
POST방식은, request.setCharacterEncoding("utf-8")을 해줘야함. 

### HttpServlet 클래스  
httpServlet도 추상클래스이다.  
그러나 추상메소드가 없는 추상클래스라서, 필요한 메소드 하나 이상만 override하면 된다.  

```java
public class ServletExample3 extends HttpServlet{

}
```

### 페이지 이동방식  
1. url 직접입력
2. link (a태그)
3. form : 입력하고 버튼을 누르면 데이터가 전송됨. (from 양식에 입력한 데이터가 submit됨)  

이 세 가지는 모두 GET방식이다.  
그러나 3번의 form은, POST로 전송한다고 명시할 수 있다.  

### 서버에서 클라이언트로 응답, 출력  
이번엔 javax.servlet.http 패키지를 보자.  
이 패키지 안에 HttpServletResponse 인터페이스가 있음.  
이 곳엔 출력 객체를 리턴하는 메소드가 없다.  
그래서, httpServletResponse의 상위 인터페이스를 방문해봄.  
ServletResponse interface를 찾아보니 getOutputStream() 메소드가 ServletOutputStream 객체를 리턴한다.  
또, getWriter() 메소드가 PrintWriter 객체를 리턴한다. 

상속 구조를 가지기 때문에 상위클래스가 가지고 있는 메소드를 사용할 수 있다.  

```java
public class ServletExample3 extends HttpServlet{
    private statid final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        PrintWriter out =  response.getWriter();
        out.println("<html>");
        out.println("   <body>");
        out.println("           HelloWorld");
        out.println("   <body>");
        out.println("<html>");
    }
}

```

### url mapping
url은 기본 주소에 root context와 @WebServlet에서 쓴 문자열이 추가된다.  
www.example.com/main/community  
이런 주소가 있다고 할 때, main은 root context이고, community는 해당 servlet에서 설정한 url이다. 
url은 일반적으로 소문자로 설정한다. 

urlPatterns = {"", "/hello"} 이런식으로 여러개를 설정할 수도 있음. 

### 한글 설정  
POST 메소드(doPost())에서 response.setContentType("text/html;charset=utf-8"); 과 같이 설정함.  

### 서블릿의 역할
1. 데이터 얻어오기 : data get
2. 일처리 : 로직에는 Business logic, Database logic이 있다.  
3. 결과 : 응답 페이지를 만든다. (html)

### 서블릿이란?
자바를 사용하여 웹페이지를 동적으로 생성하는 서버측 프로그램이나 사양.
자바 서블릿은 웹 서버의 성능을 향상시키기 위해 사용되는 자바 클래스의 일종이다. 

### 서블릿과 JSP의 차이
서블릿은 자바 코드 안에 HTML이 있다.   
JSP는 HTML 문서 안에 자바코드가 있다.  
결과적으로 JSP는 서블릿으로 변환된다.   
그러면 서블릿이 더 느릴까?  
JSP변환이 될 때 최초 한번만 변환이 된다.   

### Servlet API
서블릿 인터페이스 상속 단계 : (최상위) Servlet - GenericServlet - HttpServlet - MyServlet(커스텀서블릿)  
Request interface 상속 단계 : ServletRequest - HttpServletRequest  
Response interface 상속 단계 : ServletResponse - HttpServletResponse  


### 서블릿 라이프 사이클
서블릿 객체가 최초 생성시 한 번반 수행됨 : 생성자 -> init(Override메소드). 메모리에서 삭제될 때 destroy.  
새로고침을 누르면 doGet()만 실행됨.  

만약 사이트에, 클라이언트 수십명이 들어온다면?  
내부적으로 Thread가 열심히 일한다.  
IO나 Thread는 WAS가 처리해주기 때문에, 개발자가 크게 신경쓸 필요는 없다.  

1. request가 들어옴.  
2. Constructor 생성자로 서블릿 객체가 생성됨.  
3. init()으로 서블릿이 메모리에 로드될 때 호출되어 객체 초기화를 함.  
4. ** service(), doGet(), doPost()등이 실행됨. (모든 요청은 service()를 통해서 doXXX()메소드로 이동함)  
5. 서블릿이 메모리에서 해제되면 destory() 가 호출됨.  


### 값 여러개 받아오기
getParameterValues() 메소드는 리턴타입이 string[].  
select 버튼이나 멀티일 때 씀  
널체크를 해야함.  
 