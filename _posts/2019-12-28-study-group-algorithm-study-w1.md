---
layout: post
title: "알고리즘 스터디 1주차"
subtitle: "자료구조, 다이나믹 프로그래밍"
categories: study-group
tags: algorithm study  
comments: true
date: 2019-12-28 19:39:00 -0400
---
 

  [스타트링크 오프라인 강의](https://offline.startlink.help/hc/ko/articles/217245158)의 커리큘럼과 비슷하게 진행할 계획이라고 한다. 이번 겨울방학부터 시작해서 다음 학기에도 이어서 진행한다는 것 같다. 같은 학교 학우들과 같이 하는거라, 거리도 가깝고 연락도 쉽게 되어서 참 좋은 기회가 될 것 같다. 무엇보다 학교 공간을 쓴다는 것도 큰 장점이다. 

  1주차는 
  기본.pdf
swap
pair
scanf_s
iterator



algo.pdf

문제풀 때는 
총 연산을 생각해야한다.


점화식 사용(중요함!)
sum을 for문이 아니라 n*(n-1)/2로 사용하는 경우 
o(n)에서 o(1)로 가능



1924번 2007년

dp1.pdf
dynamic programming
분할탐색과 다른점 : dp는 탐색하려는 것들이 서로 연관없을 수도 있다.



memoization 메모이제이션

top-down : 재귀호출에 주로 쓴다. 작은 문제로 나눈다.
	기저조건 찾기
bottom-up : 이미 나와있는 케이스로 도출해보기. 점화식
(핵심!)
	처음의 작은 케이스에서 유추하기.

