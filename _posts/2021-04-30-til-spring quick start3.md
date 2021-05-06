---
layout: post
title: "[스프링 퀵 스타트] Day3 정리"
subtitle: ""
categories: review
tags: review
comments: true
date: 2021-04-30 23:20:00 -0400
---

Day3은 Model1과 Model2로 게시판을 개발한다.  
싸피에서는 3월 말에 Model2인 JSP와 서블릿으로 개발하는 법을 배웠었다.  
지난 주에 이것을 토대로 시험을 봤고, 이번주에는 Spring Lagacy와 SpringMVC를 배웠다.  

# 1-2장 Model1 아키텍처로 게시판 개발  
Controller로직을 JSP가 담당한다.  

# 3장 Model2 아키텍처로 게시판 개발  
클래스 | 구성요소
---|---
Contoller | 서블릿
Model | 자바
View | JSP페이지

# 4장 MVC 프레임워크 개발   
스프링MVC를 적용하기 전에 스프링MVC와 동일한 구조의 프레임워크를 직접 구현하여 적용함.  
| 클래스 | 기능 | 
|---|---|
| DispatcherServlet | 클라이언트의 요청 처리. FrontController |
| HandlerMappint | Controller 매핑 |
| Controller | 실질적인 클라이언트의 요청 처리 |
| ViewResolver | Controller가 리턴한 View이름으로 실행될 JSP 경로 완성 |

# 5장 Spring MVC 구조  
수행흐름

# 6-7장 Spring MVC 적용 
