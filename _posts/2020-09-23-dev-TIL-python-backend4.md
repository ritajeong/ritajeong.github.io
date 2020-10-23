---
layout: post
title: "[깔끔한 파이썬 탄탄한 백엔드] 4장 HTTP의 구조 및 핵심 요소"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-09-23 11:43:00 -0400
---

## HTTP 요청과 응답
HTTP : 요청(request)와 응답(response)의 구조로 되어있다.    

- HTTP를 기반으로 통신을 할 때  
1. 클라이언트가 먼저 HTTP 요청을 서버에 보냄.  
2. 서버는 요청을 처리함.    
3. 결과에 따른 HTTP 응답을 클라이언트에 보냄.   

그러므로 백엔드 API 시스템의 엔드포인트 구현도  
기본적으로 HTTP 요청을 input으로 받아서  
HTTP 응답을 output으로 리턴하는 구조로 구현을 하게 된다.    

```
@app.route("/ping", methods=['GET'])
def ping():
    return "pong"
```

"ping" 엔드포인트의 경우에도 마찬가지로 HTTP 요청과 응답이 오고가는 구조다.     
이 경우 HTTP 요청은 "/ping" 주소에 GET 요청을 보내는 것이고, HTTP 응답은 200 OK 상태 코드와 함께 "pong" 텍스트를 보낸다.    
