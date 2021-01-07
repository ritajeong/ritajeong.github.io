---
layout: post
title: "안드로이드 강의 레이아웃vs뷰"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-25 00:25:00 -0400
---
    
[Joyce 안드로이드 강의 CH1-1](https://youtu.be/LufIntpiuEU)    
 

### 한줄요약    
레이아웃은 뷰를 담는 그릇이다.  

Linear Layout은 필수적으로 정렬을 해줘야함.         
orientation : vertical or horizontal    
혼합의 경우 Linear Layout2를 Linear Layout1에 넣음   
그러나 많이 중첩이 되면 좋지 않음 지양해야함    

그래서 constraint Layout을 사용한다.    
장점 : Ralative Layout에서 불가능했던 자식뷰 사이의 관계 정의가능   
Linear Layout에서 레이아웃의 무게를 둬서 비율 조정했던걸 쉽게 할 수 있음.   
중첩을 최소화, 유지보수에 좋음  
