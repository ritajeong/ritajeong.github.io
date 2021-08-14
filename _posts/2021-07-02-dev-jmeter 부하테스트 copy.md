---
layout: post
title: "jmeter 부하테스트"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2021-07-02 07:33:00 -0400
---

## JMeter 실행하기
JMeter 경로로 가서 bin폴더의 jmeter.bat 파일을 클릭하여 실행해줍니다.  
<img src="/assets/img/posts/Cap 2021-07-02 07-35-23-869.jpg" width="80%" height="80%">  
File-Templates를 클릭합니다.  

## Recording  
상단의 박스에서 Recording을 클릭하고, 이어서 Create버튼을 두번 눌러줍니다.  
<img src="/assets/img/posts/Cap 2021-07-02 07-33-33-221.jpg" width="80%" height="80%">  
<img src="/assets/img/posts/Cap 2021-07-02 07-33-42-808.jpg" width="80%" height="80%">   
<img src="/assets/img/posts/Cap 2021-07-02 07-33-48-188.jpg" width="80%" height="80%">  

## Test Plan  
Test Plan을 우클릭하고, Add- Threads-jp@gc=Ultimate Thread Group을 추가합니다.  

<img src="/assets/img/posts/Cap 2021-07-02 07-33-59-688.jpg" width="80%" height="80%">  

## jp@gc-Ultimate Thread Group  
Thread Group을 펼쳐보면 Recording Controller가 있는데요, 이것을 드래그하여 jp@gc-Ultimate Thread Group으로 옮겨줍니다.  

<img src="/assets/img/posts/Cap 2021-07-02 07-34-33-192.jpg" width="80%" height="80%">  
<img src="/assets/img/posts/Cap 2021-07-02 07-34-35-415.jpg" width="80%" height="80%">  

## TPS, Response Time, Active User 추가하기  
jp@gc-Ultimate Thread Group에서 우클릭을 하고, Add-Listener에서 아래 세가지를 클릭해서 추가합니다.   
jp@gc-Active Thread Over Time, jp@gc-Response Time Over Time, jp@gc-Transactions per Second  
<img src="/assets/img/posts/Cap 2021-07-02 07-45-35-206.jpg" width="80%" height="80%">  
<img src="/assets/img/posts/Cap 2021-07-02 07-45-41-468.jpg" width="80%" height="80%">  
<img src="/assets/img/posts/Cap 2021-07-02 07-45-50-665.jpg" width="80%" height="80%">  

## HTTP(S) Test Script Recorder  
(https를 사용하신다면 미리 인증서 등록을 해주세요.)  
HTTPS Domains에 부하테스트를 진행할 사이트를 등록해주세요.  
 