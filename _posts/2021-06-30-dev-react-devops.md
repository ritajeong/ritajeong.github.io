---
layout: post
title: "React 기본페이지를 github pages로 호스팅하기"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2021-06-30 20:01:00 -0400
---

## Github Repository 생성
react-devops 의 이름으로 repository를 만들었습니다.  
<img src="/assets/img/posts/Cap 2021-06-30 20-16-53-625.jpg" width="80%" height="80%">  

## CRA로 리액트 프로젝트 생성
vscode terminal에서 아래 쓰여진 한 줄을 입력합니다.  
    yarn create react-app react-deploy-test --template typescript
<img src="/assets/img/posts/Cap 2021-06-30 20-14-05-726.jpg" width="80%" height="80%">  
완료되면 yarn start 명령어를 입력해서 사이트가 잘 뜨는 지 확인해봅시다.  

<img src="/assets/img/posts/Cap 2021-06-30 20-15-32-003.jpg" width="80%" height="80%">  
잘 뜨네요.  

## 배포
1. package.json 에 hompage 필드 추가  
  ```
  "homepage": "http://사용자이름.github.io/레포지토리이름"  
  ```
  이 문구를 package.json에 추가해주세요.  
    
  저는 아래 이미지처럼 package.json의 가장 하단부에 썼습니다.  
<img src="/assets/img/posts/Cap 2021-06-30 20-19-13-643.jpg" width="80%" height="80%">  

2. gh-pages 설치  
  vscode 터미널에서 입력하시면 됩니다.  
  ```
  yarn add gh-pages
  ```
3. package.json의 script부분에 predeploy, deploy 작성
  ```
  "predeploy": "npm run build",
  "deploy": "gh-pages -d build",
  ```
  <img src="/assets/img/posts/Cap 2021-06-30 20-23-26-663.jpg" width="80%" height="80%">  
  배열에 어긋나지 않게 콤마, 대괄호에 유의해주세요.  

3. github repository에 push해주세요.  
4. 배포
   ```
   yarn deploy
   ```
   를 터미널에 입력하고 배포해봅시다.  
  이렇게 github page url로 잘 접속되면 성공입니다.  
<img src="/assets/img/posts/Cap 2021-06-30 20-31-02-911.jpg" width="80%" height="80%">    
  