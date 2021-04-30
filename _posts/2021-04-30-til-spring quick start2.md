---
layout: post
title: "[스프링 퀵 스타트] Day2 정리"
subtitle: ""
categories: til
tags: til
comments: true
date: 2021-04-30 22:59:00 -0400
---

돌아보기 
비즈니스 컴포넌트 개발에서 가장 중요한 두 가지 원칙 : 낮은 결합도와 높은 응집도를 유지하는 것.  
DI는 결합도를 떨어뜨린다.  
AOP는 응집도를 높인다.  

Day1에서는 IoC에 속하는 개념인 DI를 배웠고, Day2에서는 AOP에 대해 배운다.  

# 1장 AOP
관심분리  
횡단관심  
핵심관심  
log 예시

# 2장 AOP 용어 및 기본 설정  
조인포인트  joinpoint 
포인트컷  pointcut  
어드바이스  Advise  
위빙  Weaving 
Aspect  

2-6그림 AOP 용어 정리  

## AOP element  
aop:config  
aop:pointcut  
aop:aspect  
aop:advisor  

## 포인트컷 표현식  
리턴타입 패키지 경로 클래스명 메소드명 매개변수 

사진추가

# 3장 어드바이스 동작 시점  
Before  
After : After Returning, After Throwing, After  
Around  

# 4장 JoinPoint와 바인드 변수  
JooinPoint 메소드  
Before 어드바이스  
After Returning 어드바이스  
After Throwing 어드바이스  
Around 어드바이스  

# 5장 어노테이션 기반 AOP  
asp:aspectj-autoproxy 설정해야한다.  
포인트컷 설정  
@Pointcut  
하나의 어드바이스 클래스 안에 여러개의 포인트컷을 설정할 수 있다.  
여러 포인트 컷을 식별하기 위한 식별자가 필요한데, 이 땐 참조 메소드를 이용한다.  
### 어드바이스 설정
### 애스팩트 설정  
@Aspect  
## 어드바이스 동작 시점  
5.2Before  
5.2 After Returning  


# 6장 스프링 JDBC  
## 6.1 스프링 JDBC 개념  
## 6.2 JdbcTemplate 클래스
## 6.3 스프링 JDBC 설정
### 6.3.1 라이브러리 추가
pom.xml에 DBCP추가 (싸피에서는 dbcp2를 사용했다.  )  
### 6.3.2 DataSource 설정  
### 6.3.3 Properties 파일을 활용한 DataSource 설정  

# 7장 트랜잭션 처리  
## 7.1 트랜잭션 네임스페이스 등록  
AOP로 처리한다.  
