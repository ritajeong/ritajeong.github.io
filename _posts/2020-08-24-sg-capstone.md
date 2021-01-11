---
layout: post
title: "Coursera Machine Learning Study Week1"
subtitle: ""
categories: sg
tags: sg
comments: true
date: 2020-08-24 16:47:00 -0400
---

안녕하세요!  
저는 이번 학기에 막학기만 남겨두고 있는 4학년 취준생입니다.  
졸업설계(=졸업프로젝트, 캡스톤)를 앞두고 있는데요,  
다행히 방학중에 팀을 먼저 구해서 스터디를 진행하게 되었습니다.	

<br>
- 8월 5일 : 첫 미팅  
이날은 서로 인사를 나누고 팀프로젝트의 방향에 대해 이야기 나눴습니다.  
신기술을 접목시킨 주제가 승인되는 경우가 많다고 들어서,  
다음 미팅까지 인공지능 기반의 아이디어를 3가지씩 생각해오기로 했습니다.	

<br>
<br>
- 8월 12일 : 아이디어 회의  
음성인식, 이미지인식, AR기반의 앱, 헬스케어, 자율주행 등..  
팀원 모두가 다양하고 재밌는 아이디어들을 가져와서  
회의가 꽤 길어졌습니다.  
카페에서 회의를 마치고, 이날은 식사도 했네요 :)  
<br>
<br>
- 8월 25일 : 코세라 스터디 시작  
기본적인 머신러닝 지식을 익히기 위해  
약 1~2주간 하루에 1주차를 끝내는 마음으로 코세라 강의를 듣기 시작했습니다.  
혼자였으면 늘어졌을 수도 있는데, 팀원들과 같이 들으니까 확실히 시너지가 나고 좋았어요.  

<br>
<br>

## 코세라 스터디 1주차
키워드 중심으로 메모하면서 들었습니다.  

### What is Machine Learning?  
경험 E의 증가에 따라 작업 T를 수행하는 작업성능P가 향상될 것이다.	

- 지도학습, 자율학습. 	
지도학습 : 작업을 수행할 수 있는 방법을 컴퓨터에게 가르치는 것이 핵심.	
비지도학습 : 컴퓨터가 스스로 학습하도록 유도	

- 강화학습, 추천시스템 =>기계학습알고리즘.	

- 도구를 활용하는 법을 배움.	

- ML,AL을 어떻게 활용하는지.	

- Tom Mitchell provides a more modern definition:	
 "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."	

	E = the experience of playing many games of checkers	<br>
	T = the task of playing checkers.	<br>
	P = the probability that the program will win the next game.	<br>

### Supervised Learning
- 학습목표 :  지도학습을 알아보고 공식적인 정의 알아봄.		 
- 기계에게 데이터셋을 주는데, 각 데이터에 정답이 있음	
회귀문제라고도 한다.	
(회귀문제 : 연속된 값을 가진 결과를 예측하려함)	 

- 또 다른 예 ) 유방암의 종양구분. 악성/양성	 
데이터셋 : 가로축 종양 사이즈, 세로축 악성1, 양성0.	 

- 표기법에 관해, X-Y축으로 표시하기보다		 
축 하나에 마크를 다르게 함. 악성x, 양성o로 표기.	 

- y축 나이, x축 종양크기, 악성/양성(x,o로 표시)    
학습 알고리즘이 해볼 수 있는 건  
데이터에 직선을 하나 맞춰서 악성/양성을 구분.  

- 무한한 수의 특성을 다루는 학습 알고리즘.   
어떻게 다루는가?  
무한대의 특성을 컴퓨터에 저장해버리면 컴퓨터 메모리 용량은 어쩌냐?  
->이후 논의할 SVM(서폿벡터머신) 알고리즘에서 수학적 방법을 사용하면 가능해진다.  

- 문제)   
case1- 팔아야하는 물건 수천개. 3개월안에 몇개나 팔릴지 예측  
case2- 고객의 계정 각각을 조사함. 해킹됐는지 판단.  
회귀문제로 봐야하는가? case1: 실수real number, 연속적인 값.   
분류문제로 봐야하는가?  case2: 해킹당했으면 1. 아니면 0. 이산값으로  


### Unsupervised Learning
- 양성 종양인지, 약성 종양인지.
- 어떤 레이블도 가지고있지 않거나, 
비지도학습은 클러스터.
- 이 데이터를 두가지 서로 다른 클러스터로 구분.
클러스터링 알고리즘.

- {클러스터링 알고리즘 C 비지도학습}의 예시  
	- 1) 알고리즘에게 데이터 집합의 예시에 대한 정답을 주지 않음.  
대규모 컴퓨터 클러스터를 구성할 때.   
데이터센터 지을 때.  
	- 2) 소셜네트워크 분석.  
	- 3) 시장 세분화. 고객의 소비정보.  
	- 4) 천문학 분석.  

- 또다른 예제. 칵테일 파티  
 칵테일 파티 알고리즘 : 더해진 두개의 녹음에서 각각의 소스를 분리해냄
한줄의 코드로 가능함  
도구 : Octave, Matlab.  
Octave로 프로토타입 만들어보기  
각각의 함수들은 예를 들어 SVD 함수는 특이값 분해의 약자.  
선형대수학 중 하나로, Octave에 내장되어있음.  
Octave로 더 빠르게 배울 수 있음.   

- 퀴즈)  
스팸 - 지도  
뉴스기사 - 클러스터링. 비지도  
시장 세분화 - 비지도.   
당뇨 - 유방암 예시. 지도  


## Model and Cost Function
### Model Representation
- 표기법 배우기  
m : 학습예제의 수.  
x : 입력 features  
y 출력값, 예측값  
(x,y)  : one training example  
(x^i, y^i) : 지수가 아님. 위첨자 i는 그냥 예제셋에서 몇번째인지, 표에서 몇번째줄인지 말하는 것이다.  

- linear function.  
h세타(x)  
선형 유형. 선형회귀 .linear regression  

### Cost Function
- 비용함수를 사용하면 주어진 데이터에 가장 가까운 일차함수 그래프를 알아낼 수 있다.  
선형증가.   
Hypothesis 함수. 가설함수.

- 선형회귀에서, 훈련집합이 있다고 해보자.  
세타0,1  
hx는 y과   
파라미터값.   
공식화  
회귀문제에서 최소값문제를 풀려고한다. 세타0,1이 각각 최소값임.  
가설의 결과값과 실제집가격의 차이의 제곱을 최소화할것임.  
x^i,y^i  
훈련집합 i=1~m까지 (시그마)  
m  
1/m  
방정식.  
선형회귀에 대한 목적함수.  
비용함수를 알아내기 위한 공식.  
세타0,1을 최소화하는 것이다.   
minimize J(세타0,세타1)  
오차요인 제곱함수는 꽤 작동을 잘 한다.  

지금까지 비용함수의 수학적인 정의를 알아봤다.   

### Cost Function
- 가설함수h세타(x), 비용함수J(세타1)  
비용함수 그래프로 알아보기  
몬소린지..  

### Cost Function 2
- 등고선 그래프. 이해할 수 있든 없든 넘어가도 좋음 어려울 수 있음   
우리가 쓰던 공식. 가설. 파라미터, 비용함수.   
비용함수의 시각화를 위해서 사용.  
가설 h와 비용함수 j.  
일차함수   
훈련집합  

비용함수 j  
활형태.  
타원형. j0,j1  
등고선.   
경사 -0.15  

## Parameter Learning
### Gradient Descent
- 기울기 하강. 선형대수, 기계학습에서 쓰임.  
min  
세타0,1의 초기값.  
초기화.  

- 등고선에서 어떻게 내려가는게 가장 빠를까?  
기울기하강. 지역최적값으로 도달  
기울기 하강의 특징 다음에 더알아보기.  

- 그래프에 대해 수학적으로 보기.  
Gradient descent algorithm    
:= 할당기호. Assignment.   
a=b Truth assetion.   
알파 : 훈련비율 learning rate. 매우크면 공격적인 하강.   
알파를 어떻게 정하는지는 나중에.   

- 미분계수. 부분 미분계수. 미분계수.  


### Gradient Descent Intuition
알파가 작으면 조금씩 이동함  

### Gradient Descent For linear regression
이전 강의에서는 기울기 하강 알고리즘을 배웠음  
선형회귀, 비용함수이 차의 제곱도 배움.  
비용함수와 기울기 하강을 함께 이용해서 선형회귀를 위한 알고리즘을 구하거나 우리 자료의 일차함수를 구해보자.  

볼록함수 convex function  
bowl shape  

batch 집단기울기하강.  
Batch Gradient Descent  
기울기하강에서 미분계수를 계산할 때 합계를 구함.  

## Linear Algebra Review
### Matrices and Vectors
인덱스 0이나 1부터 시작함  
기계학습에서는 0인덱스버전이 더 사용하기 편하다  
특별히 표시되지 않으면 1인덱스벡터.  

```matlab
Run the cell below to get familiar with the commands in Octave/Matlab. Feel free to create matrices and vectors and try out different things.  

% The ; denotes we are going back to a new row.
A = [1, 2, 3; 4, 5, 6; 7, 8, 9; 10, 11, 12]

% Initialize a vector 
v = [1;2;3] 

% Get the dimension of the matrix A where m = rows and n = columns
[m,n] = size(A)

% You could also store it this way
dim_A = size(A)

% Get the dimension of the vector v 
dim_v = size(v)

% Now let's index into the 2nd row 3rd column of matrix A
A_23 = A(2,3)
```

### Addition and Scalar Multiplication

- 더하기, 스칼라곱	


```matlab
% Initialize matrix A and B 
A = [1, 2, 4; 5, 3, 2]
B = [1, 3, 4; 1, 1, 1]

% Initialize constant s 
s = 2

% See how element-wise addition works
add_AB = A + B 

% See how element-wise subtraction works
sub_AB = A - B

% See how scalar multiplication works
mult_As = A * s

% Divide A by s
div_As = A / s

% What happens if we have a Matrix + scalar?
add_As = A + s
```


### Matrix Vector Multiplication

- 행렬*벡터

``` matlab
% Initialize matrix A 
A = [1, 2, 3; 4, 5, 6;7, 8, 9] 

% Initialize vector v 
v = [1; 1; 1] 

% Multiply A * v
Av = A * v
```


### Matrix Matrix Multiplication

- 행렬*행렬

```matlab
% Initialize a 3 by 2 matrix 
A = [1, 2; 3, 4;5, 6]

% Initialize a 2 by 1 matrix 
B = [1; 2] 

% We expect a resulting matrix of (3 by 2)*(2 by 1) = (3 by 1) 
mult_AB = A*B

% Make sure you understand why we got that result
```


### Matrix multiplication Properties

- 항등행렬

```matlab
% Initialize random matrices A and B 
A = [1,2;4,5]
B = [1,1;0,2]

% Initialize a 2 by 2 identity matrix
I = eye(2)

% The above notation is the same as I = [1,0;0,1]

% What happens when we multiply I*A ? 
IA = I*A 

% How about A*I ? 
AI = A*I 

% Compute A*B 
AB = A*B 

% Is it equal to B*A? 
BA = B*A 

% Note that IA = AI but AB != BA
```


### Inverse and Transpose

역행렬
```matlab
% Initialize matrix A 
A = [1,2,0;0,5,6;7,0,9]

% Transpose A 
A_trans = A' 

% Take the inverse of A 
A_inv = inv(A)

% What is A^(-1)*A? 
A_invA = inv(A)*A
```
