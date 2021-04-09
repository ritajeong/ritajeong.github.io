---
layout: post
title: "이클립스 및 Zulu -sun.security.ssl 관련 오류"
subtitle: ""
categories: project
tags: project
comments: true
date: 2021-04-01 22:45:00 -0400
---


- PJT 돌아보기  
지난주 : 웹 백엔드 PJT  
이번주 : 웹 DB PJT  

## 기억하기
- 오랜만에 git bash를 썼다.    
언제나 커맨드는 검색하면서 쓰게 된다...  
- 이클립스에서 import하고 나서 project fecets에서 dynamic web, java, tomcat 설정하기.  
- mysql workbench에서 erd 만들 땐 reverse engineer, 만든 erd대로 가져올 땐 forward engineer.  
- 이미 만든 테이블에서 DDL 스크립트를 뽑아낼 땐  
show create table [테이블이름];  
- csv 파일을 workbench 에서 import할 땐  
좌측의 SCHEMAS 창에서 table data import wizard를 쓰면 gui상으로 쉽게 만들 수 있다. 
- 참고한 블로그  
[블로그 1](https://blue-boy.tistory.com/23)    
[블로그 2](https://osskdb.wordpress.com/2016/08/31/)   

그러나 이것을 쓰면서 총 세 가지의 에러를 만났다.  
아래에서 이어지도록 써보자.  

## 오늘 만난 에러들  
### csv파일을 workbench에서 wizard로 import하기  
1. 로컬에 있는 파일을 직접 올릴 수 없었다.  
   [mysql 업로드 경로찾기 stackoverflow](https://stackoverflow.com/questions/32737478/how-should-i-tackle-secure-file-priv-in-mysql)  
   그래서 cmd를 켜고 mysql의 secure_file_priv 경로를 찾았더니 C:/ProgramData/MySQL/MySQL Server 8.0/Uploads 가 출력되었고, 이 곳에 csv파일을 옮겨놓았다.  

2. 그 다음엔 error code 2068(HY000)가 발생했다.  
   cmd에서 mysql 로그인을 하고 한 줄만 치면 해결되는 문제였다.  
   [set global local_infile=true;](https://stackoverflow.com/questions/63361962/error-2068-hy000-load-data-local-infile-file-request-rejected-due-to-restrict)  
3. error code 3948(42000) 는 이 블로그를 참고했다.  
    [감사한 한국인분의 블로그](https://snepbnt.tistory.com/89)  

  
### 이클립스 import에러 
1. 처음에 페어와 환경을 맞출 때, 깃허브에서 clone해오고, project fecets를 설정했는데도 잘 안됐었다.  
프로젝트 src 폴더 안에 프로젝트가 들어가는 문제  
ex)ExProject/src/ExProject 이런식으로 .. 보였었는데 이건 classpath문제였다.  
git ignore에서 classpath를 추가해주고, 각자에게 맞는 classpath를 로컬에 적용시켰더니 해결!  
2. 이건 페어분이 경험하신 오류인데, jasperException에러가 계속 떴다.  
정확한 에러메시지는"org.apache.jasper.JasperException: JSP를 위한 클래스를 컴파일할 수 없습니다." 이거였다.  
그래서 여러방법으로 import를 해보신 것 같다.  
- 첫 package explorer에서 바로 import하기,
- dynamic web project를 만들고 나서, 깃에서 clone한 프로젝트를 import하기.
Existing projects into Workspace로 프로젝트 전체를 가져왔을 때도 오류가 났었다.  
결국 해결은, File System으로 import했을 때 해결됐다.  
(맞나? 한 번 확인하기)  

