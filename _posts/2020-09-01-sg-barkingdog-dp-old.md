---
layout: post
title: "바킹독의 실전 알고리즘 구버전 0x09강 dp"
subtitle: ""
categories: ps
tags: ps
comments: true
date: 2020-09-01 08:45:00 -0400
---
스크랩한 글입니다. 
(바킹독의 알고리즘 DP) [https://blog.encrypted.gg/737?category=773649]  
중요하다고 생각되는 부분, 필요한 부분을 저장하고자 함
<br>

 0x06강에서 재귀함수로 구현했을 경우 NN번째 항을 구하는데 O(1.618^N)O(1.618 N)이 필요했지만 <br>
 DP로 구현하면 O(N)O(N)에 구할 수 있습니다.
<br>  중간 결과를 저장하는지 그렇지 않은지에 따라 이렇게 극적인 효율 차이가 만들어집니다.<br>

 코딩테스트에 나올 수준의 DP 문제는 일단 점화식만 이끌어놓고 나면 <br>그 뒤는 반복문을 돌면서 배열을 채워나가면 되기 때문에 구현이 굉장히 간단한 편에 속합니다. <br>
<br>
 https://blog.encrypted.gg/737?category=773649