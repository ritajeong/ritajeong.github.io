---
layout: post
title: "[스프링 퀵 스타트] Day1 정리"
subtitle: ""
categories: review
tags: review
comments: true
date: 2021-04-30 21:46:00 -0400
---

이번 주에는 싸피에서 스프링을 배웠다.  
스케쥴에 맞춰서 괜찮은 책 한권을 구매했고, 진도와 함께 개념 부분을 읽었다.  
이 책에서 읽은 부분 중 핵심만 간단히 정리해보려고 한다.  

# 1장 스프링 프레임워크 시작하기  
개발환경 설정으로 생략한다.  
(JDK, 이클립스, 톰캣 서버, DB, STS)  

# 2장 프레임워크 개요

## 2.1 프레임워크 개요
핵심 키워드 : 아키텍쳐, 골격 코드  
개발에서 기본이 되는 뼈대나 틀을 제공한다.  

- 개발자에게 모든 것을 위임하는 것이 아니다.  
- 애플리케이션의 기본 아키텍처는 프레임워크가 제공한다.  
- 개발자는, 이 뼈대에 살을 붙이는 작업만 한다.  

### 프레임워크 장점
- 빠른 구현 시간  
기본 뼈대가 제공되므로 개발자는 비즈니스 로직만 구현하면 된다.  
- 쉬운 관리  
  같은 프레임워크가 적용된 애플리케이션들은 아키텍쳐가 같으므로,  유지보수가 쉽다. 
- 개발자들의 역량 획일화  
  초급 개발자도 세련되고 효율적인 코드를 생성할 수 있다.  
  따라서 관리자도 개발 인력을 더 효율적으로 구성할 수 있다.  
- 검증된 아키텍쳐의 재사용과 일관성 유지  
  시간이 지나도 유지보수 과정에서 아키텍쳐가 왜곡되거나 변형되지 않는다.  


## 2.2 스프링 프레임워크  
- 복잡하고 무거운 EJB를 사용하던 시대에 등장한 스프링은, 로드 존슨이 2004년에 제시한 아키텍쳐이다.  
- 평범한 POJO를 사용하면서도 EJB에서만 가능했던 많은 일을 가능하도록 지원한다.  

### 프레임워크의 특징  
핵심 키워드 : DI, AOP  
- 경량 : 스프링은 여러개의 모듈로 구성되어있고, 각 모듈은 하나 이상의 JAR파일로 구성되어있다.  
  이 몇개의 JAR파일만 있으면 개발과 실행이 모두 가능하다.  
  따라서 애플리케이션의 배포 역시 빠르고 쉽다.  
  경량인 이유 : POJO형태의 객체를 관리하기 때문이다.  
- IoC : 제어의 역행이라고도 한다.  
  비즈니스 컴포넌트 개발시, 가장 큰 목적인 낮은 결합도와 높은 응집도를 얻게 한다.  
  IoC가 적용되지 않은 상태에서는 의존관계에 있는 객체를 변경할 때, 반드시 자바 코드를 수정해야한다.  
  그러나 IoC를 적용하면, 컨테이너가 객체 생성, 객체와 객체 사이의 의존관계를 처리한다.  
  따라서 유지보수가 편해진다.  
- AOP : 관점지향 프로그래밍  
  목적 : 높은 응집도
  어떻게 : 핵심 비즈니스 로직(핵심관심)과 반복적으로 등장하는 공통 로직(횡단관심)을 분리한다.
- 컨테이너
  하는 일 : 특정 객체의 생성과 관리를 담당하며 객체 운용에 필요한 다양한 기능을 제공한다.  
  작동 : 서버 안에 포함되어 배포 및 구동된다.  
  대표적인 컨테이너 : Servlet 컨테이너, EJB 컨테이너.
  스프링도 일종의 컨테이너로 볼 수 있다.  

## 2.3 IoC 컨데이너  
결합도(Coupling) : 하나의 클래스가 다른 클래스와 얼마나 많이 연결되어있는지를 나타낸다.  
결합도가 높은 프로그램은 유지보수가 어렵다.  

### 결합도 낮추는 법  
1. 다양한 방법이 있지만, 가장 쉽게 생각할 수 있는 건 다형성을 이용하는 것.  
상속과, 메소드 재정의(오버라이딩), 형변환이 필요하다.  
2. 디자인 패턴 이용하기  
객체 생성을 캡슐화하여 느슨한 결합상태로 만들어준다.  팩토리 패턴  

# 3장 스프링 컨테이너 및 설정 파일  
### scope 속성  
singleton : 컨테이너당 단 하나만 생성.(디폴트)  
prototype : 컨테이너에 빈을 요청할 때마다 새 인스턴스 생성.   
request : HTTP Request별로 새 인스턴스 생성.    
sessinon : HTTP Session별로 새 인스턴스 생성.   
더 큰 범위 : application, WebSocket.  

# 4장 의존성 주입(DI)  
- 의존성(Dependency) : 객체와 객체의 결합관계  
  하나의 객체에서 다른 객체의 변수나 메소드를 이용해야 한다면 이용하려는 객체에 대한 객체 생성과 객체의 레퍼런스 정보가 필요하다.  
DI는 IoC의 핵심원리  
DI에는 xml, annotation, java configuration 이렇게 3가지 방법이 있다.  
이 책에서는 4장에서 xml방법을 다루고, 5장에서 annotation을 다룬다.  
java configuration은 주로 스프링 부트에서 사용한다.  

## IoC 형태  
1. Dependency Lookup : 컨테이너가 객체를 생성하고, 클라이언트는 컨테이너가 생성한 객체를 검색(Lookup)하여 사용하는 방식  
2. Dependency Injection : 객체 사이의 의존관계를 설정 파일에 등록하면, 이를 바탕으로 컨테이너가 자동으로 처리한다.  
   따라서 의존성 설정을 바꾸고 싶을 때 프로그램 코드를 수정하는 것이 아닌, 설정 파일 수정만으로 변경할 수 있다.  
   Setter 메소드 기반의 Setter Injection과 생성자 기반의 Constructor injection이 있다.  

### Constructor Injection  
xml 설정 파일에 등록된 클래스를 찾아서  
객체 생성시 기본적으로 디폴트 생성자를 호출함.  
매개변수 생성자를 호출하도록 설정할 수 있다. 
- 매개변수 생성자 예시

<bean id="tv" class="polymorphism.SamsungTV">  
  <constructor-arg index="0" ref="sonny"></constructor-arg>  
  <constructor-arg index="1" value="27000000"></constructor-arg>    
</bean>    

ref 속성 :  객체의 아이디나 이름을 참조함  
value 속성 : 고정된 문자열이나 정수 같은 기본형 데이터일 때 
index 속성 : 어떤 값이 몇번째 매개변수로 매핑되는지 지정할 수 있다.  
이 땐, 매개변수의 순서를 지정하거나 

### Setter Injection  
Setter 인젝션은 <constuctor-arg> 엘리먼트 대신 <property> 엘리먼트를 사용한다. 
property 엘리먼트에서 name 속성값이, 호출하고자 하는 메소드 이름이다.  
name 속성값이 "speaker"이면 호출되는 메소드는 setSpeaker()이다.  
Setter 메소드가 제공되지 않는 클래스에 대해 생성자 인젝션을 사용한다.  
보통은 Consructor Injection, Setter Injection중 하나로 통일해서 사용한다.  

### 컬렉션 객체 설정  
- List 타입 매핑  
- Set 타입 매핑 : 중복을 허용하지 않는 집합 객체  
- Map 타입 매핑 : 특정 키로 데이터를 등록할 때  
- Properties 타입 매핑 : key=value 형태의 데이터를 등록할 때  

# 5장 어노테이션 기반 설정  

- Context 네임스페이스 추가  
annotation 설정을 추가하려면 설정 파일의 루트 엘리먼트인 <beans>에 Context관련 네임스페이스와 스키마 문서의 위치를 등록해야한다.  
Namespace 탭을 선택하고 context항목만 체크하면 간단히 추가할 수 있다.  

- 컴포넌트 스캔 설정  
  context:component-scan 엘리먼트를 정의한다.  
  클래스 패스에 있는 클래스들을 스캔하여 @Component가 설정된 클래스들을 자동으로 객체 생성한다.  
  base-package속성을 지정하면, 하위 모든 패키지들이 대상이 된다.  

## 5.2 의존성 주입 설정  
### 의존성 주입 어노테이션  
@Autowired, @Qualifier, @Inject, @Resource가 있다.  
앞에 두가지는 스프링에서 제공하지만, 나머지는 아님.  

- @Autowired  
  가장 많이 쓰임.  
  생성자나 메소드, 멤버변수 위에 모두 사용가능.  
  어디에 사용하든 결과는 같지만, 대부분 멤버변수 위에 선언하여 사용함.  

## 5.3 추가 어노테이션  
| 어노테이션 | 위치 | 의미 |
| ---|---|---|  
|@Service|XXXSeriviceImpl|비즈니스 로직을 처리하는 Service 클래스|  
|@Repository|XXXDAO|데이터베이스 연동을 처리하는 DAO 클래스|  
|@Controller|XXXCotroller|사용자 요청을 제어하는 Controller 클래스|    

- 어노테이션을 나누는 이유  
  단순히 해당 클래스를 분류하기 위해서만은 아니지만, 이 장에서는 이정도로만 이해하고 넘어가는 게 좋다.  
  @Controller는 해당 객체를 MVC 아키텍처에서 컨트롤러 객체로 인식하도록 해준다.  
  @Repository는 DB 연동 과정에서 발생하는 예외를 변환해주는 특별한 기능이 추가되어있다. 



# 6장~7장 비즈니스 컴포넌트 실습1,2  
6장에서는 게시판 기능의 DTO(VO), DAO, Service 를 작성한다.  
DTO는 데이터베이스의 테이블 구조에 맞게 private 으로 멤버변수를 생성하고, getter와 setter함수, toString 함수를 작성한다.  
DAO에서는 CRUD기능의 메소드를 구현한다. 이 때 JDBC드라이버가 필요하다.  

7장에서는 회원관리기능을 작성한다.  