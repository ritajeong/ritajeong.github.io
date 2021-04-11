---
layout: post
title: "이클립스 및 Zulu -sun.security.ssl 관련 오류"
subtitle: ""
categories: dev
tags: dev
comments: true
date: 2021-04-01 22:45:00 -0400
---

<img src="\assets\img\posts\20210401.jpg">  

이클립스 2018-09버전과 Zulu(자바8)를 사용하면서 근 한달간 sun.security.ssl 오류를 겪었다.   
우선 이클립스를 켜면 gradle 시동중에 에러가 생겼다고 메시지가 뜨고,  
그 이후에도 ctrl c, v, space 등의 단축키를 쓰거나  
자동 import를 할 때마다 간헐적으로 발생했다.  
또한 마켓플레이스와 intall new software는 아예 사용이 불가능했다.  

프로젝트 실행에 직접적으로 영향을 미치는 건 없었어서 불편함을 감수하고 코딩을 해왔다.  
그러나 결정적으로 jdbc를 연동하는 데 문제가 생겼고,  
갈아엎기 시작했다.  

mysql workbench를 2번 재설치 했다.  
콘솔창에 뜨는 오류메시지를 보니 동일하게 sun.security.ssl ...문구가 있었다.  
그래서 이클립스를 재설치했다.  
완전삭제, 설치를 반복해도 여전히 그대로였고,  
2020-03버전을 설치해도 마찬가지였다.  

마지막으로 zulu 재설치를 진행했더니 해결되었다.  
개발환경 문제는 정말 골치아프다.  
다시는 이런 일을 겪고 싶지 않다.  
이번건 참 재수없게도 관련된 레퍼런스나 특별한 검색자료가 있지도 않아서 더 고생스러웠다.  



jdbc에서 연동에서 겪었던 에러 로그

```
Exception in thread "main" java.lang.ExceptionInInitializerError
    at javax.crypto.JceSecurityManager.<clinit>(JceSecurityManager.java:65)
    at javax.crypto.Cipher.getConfiguredPermission(Cipher.java:2586)
    at javax.crypto.Cipher.getMaxAllowedKeyLength(Cipher.java:2610)
    at sun.security.ssl.CipherSuite$BulkCipher.isUnlimited(CipherSuite.java:535)
    at sun.security.ssl.CipherSuite$BulkCipher.<init>(CipherSuite.java:507)
    at sun.security.ssl.CipherSuite.<clinit>(CipherSuite.java:614)
    at sun.security.ssl.SSLContextImpl.getApplicableSupportedCipherSuiteList(SSLContextImpl.java:294)
    at sun.security.ssl.SSLContextImpl.access$100(SSLContextImpl.java:42)
    at sun.security.ssl.SSLContextImpl$AbstractTLSContext.<clinit>(SSLContextImpl.java:529)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:264)
    at java.security.Provider$Service.getImplClass(Provider.java:1634)
    at java.security.Provider$Service.newInstance(Provider.java:1592)
    at sun.security.jca.GetInstance.getInstance(GetInstance.java:236)
    at sun.security.jca.GetInstance.getInstance(GetInstance.java:164)
    at javax.net.ssl.SSLContext.getInstance(SSLContext.java:156)
    at com.mysql.cj.protocol.ExportControlled.getSSLContext(ExportControlled.java:620)
    at com.mysql.cj.protocol.ExportControlled.performTlsHandshake(ExportControlled.java:303)
    at com.mysql.cj.protocol.StandardSocketFactory.performTlsHandshake(StandardSocketFactory.java:188)
    at com.mysql.cj.protocol.a.NativeSocketConnection.performTlsHandshake(NativeSocketConnection.java:97)
    at com.mysql.cj.protocol.a.NativeProtocol.negotiateSSLConnection(NativeProtocol.java:333)
    at com.mysql.cj.protocol.a.NativeAuthenticationProvider.connect(NativeAuthenticationProvider.java:167)
    at com.mysql.cj.protocol.a.NativeProtocol.connect(NativeProtocol.java:1350)
    at com.mysql.cj.NativeSession.connect(NativeSession.java:157)
    at com.mysql.cj.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:953)
    at com.mysql.cj.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:823)
    at com.mysql.cj.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:453)
    at com.mysql.cj.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:246)
    at com.mysql.cj.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:198)
    at java.sql.DriverManager.getConnection(DriverManager.java:664)
    at java.sql.DriverManager.getConnection(DriverManager.java:247)
    at com.ssafy.jdbc.JdbcTest.main(JdbcTest.java:21)
Caused by: java.lang.SecurityException: Can not initialize cryptographic mechanism
    at javax.crypto.JceSecurity.<clinit>(JceSecurity.java:93)
    ... 32 more
Caused by: java.lang.SecurityException: Cannot locate policy or framework files!
    at javax.crypto.JceSecurity.setupJurisdictionPolicies(JceSecurity.java:316)
    at javax.crypto.JceSecurity.access$000(JceSecurity.java:50)
    at javax.crypto.JceSecurity$1.run(JceSecurity.java:85)
    at java.security.AccessController.doPrivileged(Native Method)
    at javax.crypto.JceSecurity.<clinit>(JceSecurity.java:82)
    ... 32 more
    ```