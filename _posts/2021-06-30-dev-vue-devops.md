---
layout: post
title: "Vue 기본페이지를 github로 호스팅시 발생한 github 토큰문제"
subtitle: ""
categories: dev
tags: dev
comments: true
date: 2021-06-30 20:01:00 -0400
---

## 직면한 문제  
github actinos에서 deploy.yml을 만들고, 변경사항을 push하려는데 remote rejected 에러가 발생했다.  
<img src="/assets/img/posts/Cap 2021-06-30 20-53-45-802.jpg" width="80%" height="80%">  
에러메시지를 구글링해보니 깃허브 토큰 문제라고 한다.  
[깐깐한 조부장 블로그](https://director-joe.kr/91) 를 참고하여 해결했다.  

## 이유
github 계정- Settings-Personal access tokens에서 토큰을 생성하고 다시 지정하라는데,  
이 곳에서 토큰 만들기를 해보면 repo, workflow, gist..등을 체크할 수 있다.  
<img src="/assets/img/posts/Cap 2021-06-30 21-46-25-159.jpg" width="80%" height="80%">  
내가 만들어뒀던 토큰엔 workflow가 없어서 발생한 문제였다.   


## 해결
토큰을 새로 만들어야하나? 고민했는데,
그냥 윈도우 자격증명에서 github와 연결된 것들을 다 제거하고  
git bash에서 push를 했더니 github와 새로 연결하는 페이지가 열렸다.  
그리고 push했더니 성공!  


## 참고
- 참고한 사이트 [깐깐한 조부장 블로그](https://director-joe.kr/91)