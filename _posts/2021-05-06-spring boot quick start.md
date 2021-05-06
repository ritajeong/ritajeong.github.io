---
layout: post
title: "[스프링 부트 퀵 스타트] 정리"
subtitle: ""
categories: review
tags: review
comments: true
date: 2021-05-06 22:32:00 -0400
---

# 6. 스프링 부트 화면 개발  
## 6.1 화면개발  
타임리프 : 스프링 부트가 지원하는 템플릿 엔진.  
이것을 이용하면 데이터와 완벽하게 분리된 화면을 개발할 수 있다.  
따라서 순수한 html파일만을 이용한 화면개발이 가능하다.  
운영과정에서 쉽게 화면을 변경할 수 있다.  

최종적으로 타임리프를 적용하고, 우선은 jsp를 이용하여 간단히 화면 구성을 한다.  

### 6.1.1 실습 프로젝트 생성 및 환경 설정하기  
- jstl 의존성 추가  
pom.xml에 jsp에서 jstl을 사용하기 위해 jstl에 대한 의존성을 추가한다.  
gradle일 경우 build.gradle에 추가한다.  

- ViewResolver  
목적 : jsp 파일의 위치와 확장자를 제어하기 위해  

applications.properties에 아래 두 줄을 추가한다.    
spring.mvc.view.prefix=/WEB-INF/views  
spring.mvc.view.suffix=.jsp  

그러면 메모리에 생성된 ViewResolver는 src/main/wepapp 밑에 있는 WEB-INF/views 폴더의 jsp파일을 뷰로 사용한다.  


applications.properties를 쓸 때 주의점 : 문장 끝 공백 x, =기호 전후로 공백x  

- 롬복 : Dto에 Getter, Setter, ToString 어노테이션만 붙여주면 된다.  
- JSTL : taglib, forEach 등. 
- EL : 값을 출력할 때 사용.  

## 6.2 타임리프 적용  
JSP 기반의 화면 개발 대신 타임리프 같은 템플릿 엔진을 사용하여 화면을 개발할 수 있다.  
사용자에게 제공되는 화면과 데이터를 분리하여 관리할 수 있다.  
템플릿은 HTML과 같은 마트업이고, 데이터는 데이터베이스에 저장된 데이터이다.  
결국, 템플릿 엔진을 이용하여 화면을 처리하면 고전됭 데이터에 다양한 템플릿을 적용할 수 있다.  

- 타임리프 의존성 추가 : 스프링 스타터에서 추가가능  
- 서버 내부의 캐시는 디폴트로 true로 되어있어서, 개발된 화면을 수정했을 때 매번 프로젝트를 다시 실행해야한다.  
따라서 application.properties에 spring.thymeleaf.cache=false 를 추가해준다.     
- src/main/resources/template 폴더에 html을 생성하고, html에 타임리프 네임스페이스를 선언한다.  
- 이클립스에서(STS)  타임리프 플러그인을 설치한다.  
#### 6.2.2.1  게시글 목록 출력하기      
th:each속성 : JSTL의 <c:forEach> 와 같은 기능을 한다. 

### 6.3.2 예외 처리  
사용자의 부주의나 시스템 운영과정에서 발생된 문제에 대해, 적절한 처리와 함께 관련된 화면을 사용자에게  제공한다.  
#### 6.3.2.1 사용자 정의 예외 발생하기
(1) 예외의 개념
자바는 시스템에서 발생되는 문제를 에러(Error)와 예외(Exception)으로 구분한다.  
시스템 에러는 개발자가 제어할 수 없는 문제이므로 제외하고 우리가 관리할 수 있는 예외에 집중한다.  

#### 스프링에서 예외를 처리하는 두 가지 방법 
1. @ControllerAdvice 어노테이션을 이용하여 모든 컨트롤러에서 발생하는 예외를 일괄적으로 처리함.  
   (전역 예외처리라고 하며, 일반적으로 많이 사용한다.)  
2. @ExceptionHandler 어노테이션을 이용하여 각 컨트롤러 마다 발생하는 예외를 개별적으로 처리  
   (로컬 예외처리)  


(2) 사용자 정의 예외  
예외를 처리하려면 우선 문제가 발생될 만한 상황에서 예외를 발생시킬 수 있어야한다.  
1. 체크드 예외(Checked Exception)  
   컴파일 시점에 발생  
2. 언체크드 예외(Unchecked Exception)  
    컴파일은 통과하지만 실행 시점에 발생하는 예외.  

(3) 예외 발생하기  
예외를 강제로 발생시키도록 ExceptionController를 작성한다.  

#### 6.3.2.2 예외 처리하기  
(1) 예외 처리기 작성  
모든 예외에 대해 적절한 예외 화면을 연결해주는 전역 예외 처리기를 만든다. (GlobalExceptionHandler.java)  
@ControllerAdvice 어노테이션을 GlobalExceptionHandler 클래스에 선언한다.  
그리고 발생된 예외의 타입에 따라 다양한 화면이 처리되도록 @ExceptionHandler를 가진 메소드를 여러개 선언한다.  



