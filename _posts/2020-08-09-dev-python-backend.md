---
layout: post
title: "[깔끔한 파이썬 탄탄한 백엔드] 1장"
subtitle: "1장 실습"
categories: dev
tags: til
comments: true
date: 2020-08-09 19:01:00 -0400
---


## 1장 파이썬 설치 및 개발환경구성
- 본격적인 설치에 앞서 : 운영체제에 대한 간략한 소개.   
나는 가상머신에서 우분투를 쓰기로 정했다.   
- 파이썬 설치 : 유의점-버전 2과 3은 호환되지 않아요 
- 파이썬 가상환경설치 : miniconda3  
콘다란 ? 파이썬 패키지 매니저와 개발 환경 매니저 기능을 제공하는 개발 툴이다.   
Anaconda에서 만든 파이썬 배포판ㄴ에 포함되어있다.   
Anaconda는 데이터 분석 및 사이언스에 특화된 파이썬 배포판으로 Numpy, SciPy 등 다양한 패키지가 미리 설치되어 나온다.     
- 터미널 환경 : CLI에 익숙해지라고 권고한다.    
Gnome 터미널이 디폴트이고, Gogh를 이용해서 터미널 색상 테마를 변경할 수 있다.   
- 깃 : Git, TIG(깃 커밋 히스토리를 터미널에서 보여주는 툴), Diff So Fancy(git diff의 출력화면을 더 보기 쉽게 해주는 플러그인)   
- 셸 : bash, ZSH, oh my zsh         
셸 ? 터미널 환경에서 운영체제의 커널과, 사용자의 유저스페이스를 이어주는 인터페이스 역할을 하는 프로그램이다.(31p)  
셸스크립트라는 셸 전용 프로그래밍 언어를 사용해서 터미널 환경에서 다양한 자동화를 실행할 수 있다.   

- 다양한 에디터 소개 : 파이참, VSCode, VIM, Sublime Text    
    IDE는 다양한 기능들을 제공해주므로 편리하긴 하지만, 그 편리함 때문에 언어의 숙련도를 높이는 데 방해가 되기도 한다.  
    그에 반해 VIM은 기본적으로 편집 기능만 제공하므로 해당 언어나 개발환경은 사용자가 직접 찾아보고 익숙해져야한다. 
    그러므로 처음에는 개발속도가 느릴 수 있지만, 시간이 지남에 따라 해당 언어와 개발환경에 관해 많은 것들을 배우게 된다.    
    그러한 이유로 저자는 VIM을 추천한다.(41p)   

    서브라인 텍스트는 파이참처럼 무겁거나 VIM처럼 어려운 에디터가 아니다.   
    사용하기 쉽고 꼭 필요한 기능을 다 제공하면서도 복잡하지 않아 인기가 많다.   
    게다가 무료임.


<img src="/assets/img/posts/2020-08-09.png" width="50%" height="50%">  
<br>
<img src="/assets/img/posts/2020-08-09-2.png" width="50%" height="50%">  
<br>
<img src="/assets/img/posts/2020-08-09-3.png" width="50%" height="50%">  
<br>
<img src="/assets/img/posts/2020-08-09-4.png" width="50%" height="50%">  
<br>
<img src="/assets/img/posts/2020-08-09-5.png" width="50%" height="50%">  
<br>
<img src="/assets/img/posts/2020-08-09-6.png" width="50%" height="50%">  