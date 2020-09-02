---
layout: post
title: "컴퓨터보안 1주차"
subtitle: ""
categories: dev
tags: TIL
comments: true
date: 2020-09-02 23:50:00 -0400
---

1.  보안의 3요소 : CIA
- 기밀성 ( Confidentiality )
- 무결성 ( Integrity )
- 가용성 ( Availability )

2. 암호학은 크게 두 분류로 나뉨 
- 대칭암호 : 블럭암호가 많이 쓰인다. 난수생성, 스트림, 해시함수, 메시지 인증 등
- 공개키 : 대표적으로 RSA, 전자서명. 송수신자간 통신에 있어서 안전하게 쓰이기 어렵다. 대안으로 key exchange가 쓰임. 

3. 접근제어 정책과 메커니즘 
- 주체가 누군지 먼저 확인해야함.    

4. 공격에 자주 쓰이는 기법
- buffer overflow, fuzzing. 
- malware
- network based attack, port scanning, spoofing, packet sniffing, denial service, ARP
- web기반 공격 : phising, click jacking, XSS, SQL injection
- sns기반 공격
- large scale : 고도화된 공격들. botnet, zero-day attack
- anonymity network : Tor
- vulnerability DB

5. 그외 주제
- 정보정책, CISO, 감사(Audit)
- 디지털 포렌식
- CERT : 침해사고 대응팀
- 인증과 표준 : CMVP, KCMVP
- 법제도 : 데이터3법
- 전자서명법
- 전자정부법
- 유럽 GDPR

