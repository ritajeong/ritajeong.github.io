---
layout: post
title: "Coursera Machine Learning Study Week2"
subtitle: ""
categories: project
tags: project
comments: true
date: 2020-08-30 16:49:00 -0400
---

코세라 머신러닝 스터디 2주차를 학습했습니다.	
강의를 듣자마자 바로바로 문제를 푸는 게 매우 효과적인데,	
테스트가 늦게 열려서 지장이 있었습니다.	
<br>
저는 키워드를 메모하면서 공부하는 방식이 잘 맞는 편입니다. 	
그러나 이번 스터디는 빠른 시일 내에 들어야해서,		
(과제도 오래걸리기도 하고..)	
교수님이 말하신 멘트 중 중요한 문장을 스크랩하는 식으로 공부하려합니다. 	

# Multivariate Linear Regression
## Multiple Features
- 학습목표 : 하나 이상의 변수나 feature를 다루기 위한 더 강력한 선형회귀에 대해 알아보자

## Gradient Descent for Multiple Variables
- 학습목표 : 여러 요소들의 선형 회귀에 경사 하강법을 적용하는 지도 알아보도록 하겠습니다.
<br><br>

## Gradient Descent in Practice I - Feature Scaling
- 학습목표 : gradient descent를 잘 활용할 수 있는 몇 가지 방법들을 알려주고자 합니다. <br>
- 이번 시간에는 먼저 feature scaling이라고 하는 것을 배운다.
<br> 
- 개념은 이렇습니다. <br>만약 여러개의 feature가 있고, feature의 단위크기가 비슷하다면, 이 말은 즉, 서로 다른 feature라도 범위가 같다면
<br>
gradient descent는 더 빠르게 수렴할 수 있습니다.<br><br>
 
범위는 -1~1사이.<br>
그와 비슷하게 -3~3정도까지도 괜찮다. or -1/3~1/3.<br>
그러나 -100~100처럼 너무 크거나 너무 작으면 안됨<br>

### Mean normalization
- 평균을 0으로 만들어 scale을 줄이는방법.

## Gradient Descent in Practice II - Learning Rate
- 학습목표 : debugging- gradient descent가 잘 돌아가게 하기 위한 방법<br>
- 두 번째로는, learning rate 알파를 고르는 방법 즉 어떤 값으로 시작할지에 대해 이야기해보겠습니다.<br>

<br>
- gradient descent의 목적은 cost function J（θ）가 최소화되는 θ의 값을 찾는 것<br>
<br>
400번 반복후에는, gradient descent는 거의 거의 수렴한 것입니다.<br> cost function이 더 이상 줄어들지 않기 때문입니다. <br>이렇게 그래프를 보면 gradient descent가 수렴하였는지 아닌지 알 수 있습니다.<br><br>

보통은 그래프를 그리고, 반복 횟수의 증가에 따라 cost function을 그려서, <br>그래프를 보며 gradient descent가 수렴하는지 아닌지를 봅니다.<br> 수렴하는지 아닌지 자동으로 검사하는 방법(automatic convergence test)도 있습니다.<br> 즉 지금 gradient descent가 수렴하는지 알려주는 알고리즘입니다. 
<br><br>
실제로 J(θ)가 증가하는 일은, 보통 어느 함수를 최소화 하려고 할 때 일어납니다.<br> 이렇게 생긴 함수를요.<br>
<br><br>
알파가 너무 작으면, 이 점에서 시작했을 때 아기가 기어가는 느낌을 받을 것입니다. <br>수 차례 반복하고 나서야 최소값에 도달하게 됩니다. <br>즉 알파가 너무 작으면, gradient descent는 천천히 진행하면서 천천히 수렴하게 됩니다.<br> 정리하면, learning rate가 너무 작을때는 천천히 수렴한다는 문제가 있고, learning rate가 너무 크면 J(θ)가 매 반복마다 감소하지 않고 심하면 수렴하지 않습니다. <br>learning rate가 너무 큰 경우에, 천천히 수렴하는 문제가 발생할 수도 있습니다. <br><br>
(퀴즈)
<br>
저 같은 경우 가능한 가장 작은 값과 가장 큰 값을 찾습니다. <br>그리고나서, 다음으로 가능한 가장 큰 값이나 가장 큰 값에서 조금 작은 값을 선택합니다. <br>저는 이렇게, 적절한 learning rate를 찾습니다. <br>여러분들도 이렇게하여, 적절한 learning rate를 찾고, gradient descent를 구현할 수 있습니다.<br>
<br>

## Features and Polynomial Regression
- 학습목표 : feature를 간단하게 선택하는 방법과 적절한 feature의 선택으로 강력한 학습 알고리즘을 만드는 방법에 대해 이야기해보겠습니다.<br>
<br>
즉, 문제를 어떻게 이해하느냐에 따라, 곧이곧대로 feature를 쓰는것보다는 때로는 새로운 feature로 더 나은 모델을 정의해도 좋습니다. <br>
feature를 선택하는 것과 밀접하게 관련된 것으로 다항 회귀(polynomial regression)가 있습니다. <br>
<br>
하지만 이 2차식 모델은 사실 적합하지가 않습니다. <br>왜냐하면 이 함수는 결국 하강하기 때문입니다.<br> 집 크기는 커지는데, 집 값은 작아질리는 없죠
2차 함수 대신에, 3차식을 이용하여 표현하면, 이러한 모양의 모델이 나오고, 이번에 초록색 선은 data를 더 잘 표현합니다.<br> 왜냐하면 이번에는 하강하지 않기 때문입니다. <br><br>

두 식이 같아지도록 하기 위해서는, 첫 번째 feature x_1은 집의 크기로 치환하고, 두 번째 feature x_2는 집의 크기의 제곱으로 치환하고, 세 번째 x_3는 집의 크기의 세제곱으로 치환합니다. <br>
이와 같이 세 개의 feature를 선형 회귀형태로 적용시키면, 이 모델을 삼차식으로 표현할 수 있습니다. <br>한 가지 더 강조하고 싶은 것은 이렇게 feature를 선택했을 때, eature scaling의 적용은 훨씬 더 중요해진다는 것입니다.<br><br>

결국 이 세 개의 feature는 매우 다른 값의 범위를 가지게 되므로, feature scaling을 적용시키는 것이 중요합니다. <br>
그래야 gradient descent를 할 때 서로 비슷한 범위를 가질수 있습니다. <br>
<br>
그럼, 마지막으로 feature를 다루는 다양한 방법을 보여주는 예제를 들어보겠습니다. <br> 처음에, 이러한 2차식 모델은 이상적이지 않다고 말했는데, data를 표현하는데는 괜찮지만, 2차 함수는 하강하는 모양이고, 그런 모양은 우리가 원하는 모양이 아니기 때문이였습니다. <br>하강하는 모양이라면, 집의 크기가 폭등할 때, 집 값은 떨어지는 것으로 예측됩니다. 그래서 3차 식 모델을 소개했지만, 그것 말고도 다른 방법이 있습니다. <br>다른 괜찮은 방법 중 한 가지 예를 들어보면, 그 예는 집 값을 θ_0 + θ_1 ##(크기) + θ_2*(크기의 제곱근)으로 나타내는 것입니다. <br> 제곱근 함수는 이런 모양입니다. <br>그리고, θ_0, θ_1, θ_2의 값이 있으면, 이러한 모델이 만들어질 것입니다. 이 곡선은 갈수록 이렇게 평평해지지만 하강하지는 않습니다.<br> 결국, 문제를 다른 관점에서 본다면, 이 경우에서는 data의 모양을 제곱근 함수의 관점에서 본다면, feature를 가지고 더 나은 모델을 만들 수 있습니다. <br><br>

여러개의 서로 다른 feature가 있을 때는, 어떤 feature를 사용해야하는지 혼란스러운 상황이 있을 수도 있습니다.<br> 이 수업 이후에, 자동으로 어떤 feature를 사용할지 골라주는 알고리즘에 대해서 배울 것입니다. <br>
그 알고리즘은 data를 보고, 자동으로 2차 함수나 3차 함수, 혹은 다른 함수들 중 알맞은 것을 선택합니다. <br>하지만, 이 알고리즘을 배우기전인 지금, 어떤 feature를 사용할지는 여러 방법이 있다는 것을 알아두었으면 합니다. <br>그리고, 다른 feature를 고안하여, data를 직선으로 표현하는게 아닌 복잡한 함수로 표현할 수 있습니다. 특히, 다항 함수나 때로는, 적절한 feature로 더 나은 모델을 새울 수 있습니다.<br>

## Normal Equation
<br>
- 학습목표 :  normal equation에 대해 배워보겠습니다. <br>특정 선형 회귀 문제에서, 파라미터 θ의 최적의 값을 구하는데 효과적인 방법입니다. <br>
<br>
normal equation도 장점과 단점이 있지만, 장단점과 사용시기를 말하기 전에, 어떠한 함수인지 개념을 알아 봅시다.<br><br>

- cost function J(θ) <br>
Cost function J는 실수 파라미터 θ에 대한 2차 함수라고 해봅시다. <br>
2차 함수를 최소화 하는 방법은 무엇일까요? <br>미적분을 배웠다면, 함수를 최소화하기 위해 미분을 하고,<br> 미분값이 0이 되는 지점이 답이라는 것을 알 수 있습니다. <br><br>

미분값이 0일 때, J(θ)가 최소화되는 θ를 구할 수 있습니다. <br>data가 실수일 때 가능한 경우였습니다.<br> 우리가 흥미롭게 다루어볼 문제는, θ가 더 이상 실수가 아니라 (n+1)차원 파라미터 벡터일 때입니다.<br>
cost function J도 벡터 값에 대한 즉, θ_0부터 θ_m까지에 대한 함수입니다. <br>cost function은 이렇고, 오른쪽은 제곱함수입니다. <br>cost function J를 어떻게 최소화 할 수 있을 까요? <br>미적분을 이용한다면, 한 가지 방법으로 J를 편미분하는 방법이 있습니다. <br>각각 모든 파라미터 θ_j에 따라서 차례차례로 미분하고, 모두 0이 되게 합니다. <br>그렇게 하면, 모든 θ에 대한 답을 구할 수 있습니다. <br>θ_0, θ_1, θ_n까지요. <br>그리고나서, 그 때의 θ를 대입하면, cost function J를 최소화 할 수 있습니다.<br>


이 번 비디오에서는 미분을 사용하여, 답을 구하지 않을 것입니다. <br> 미분은 시간이 오래 걸리는 방법입니다. <br> 하지만, 이 과정을 구현하기 위해서는 알아야 할 것이 있습니다. <br> 그러면, 편미분 방정식이 0이 되는 θ 값을 구할 수 있습니다. <br> 같은 말이지만, 다르게 말하면, cost function J(θ)가 최소화 되는 θ를 구하는 것입니다. <br>

이번에 다룰 내용은 미적분학에 익숙치 않은 사람에게 생소할지도 모릅니다. <br> 하지만, 이해가 잘 안되거나, 미적분에 낯설지라도, 걱정할 필요없습니다. <br> 알고리즘을 구현하고 적용하는데 필요한 것들은 알려드릴 겁니다. <br> 이 예제는, 이 번에 다루어볼 예제입니다. <br> m=4인 training example이 있습니다. <br>

<br>
해야할 것은 data set에 열을 추가하는 것입니다. <br> 추가된 열은 feature x_0입니다. <br> 모두 1의 값을 가집니다. <br> 그 다음으로는 X라는 행렬을 만드는 것입니다. <br> 행렬 X는 training data의 모든 feature를 가지고 있습니다. <br> 즉 이것은 모두 feature이고, 이 숫자들은 전부 행렬 X에 넣습니다. <br> 
결국 X는 
<br>

(m x n+1) 차원 행렬이 되었고 y는 m차원 벡터가 되었습니다. <br> m은 training example의 수이고, n은, n은 feature의 수입니다. <br> n+1인 이유는 여기 추가로 feature x_0이 있기 때문입니다. <br> 
(문제스샷)

이전 비디오에서 feature scaling을 자세히 배웠는데, feature의 범위를 비슷한 범위로 조절하여 각각 비슷한 값의 범위를 가지도록 하는 것입니다. <br>
<br>

일반적인 경우를 보면, m개의 training example에서 ( x^(1) , y^(1) )부터 ( x^(n), y^(n) )까지 n개의 feature가 있습니다. <br> 그리고, 각각의 training example x^(i)는 이와 같은 벡터입니다. <br> (n+1)차원 feature 벡터죠 이제 행렬 X를 만들어 볼 것입니다. <br> 행렬 X는 design matrix라고도 하며, 이와 같이 만듭니다. <br> 각각의 training example은 이와 같은 feature 벡터로 나타낼 수 있습니다. <br> (n+1)차원 벡터죠 design matrix X를 만드는 방법은 이렇습니다. <br> 우선 첫 번째 training example, 즉 벡터죠. <br> 벡터를 transpose하여, 이렇게 넣습니다. <br> 이렇게 가로로 퍼진 형태가 되고, x^(1)을 transpose한 것이 design matrix의 첫 번째 열이 됩니다. <br>

이제 두 번째 training example x^(2)를 보죠. <br> transpose하고, X의 두 번째 열에 넣습니다. <br> 나머지도 이런식으로 해서, 마지막 training example까지 내려갑니다. <br> 마지막을 transpose하여 행렬 X의 마지막 열로 만듭니다. <br> 이렇게 행렬 X를 만듭니다. <br> X는 (m x n+1)차원 행렬이죠. <br> 

마지막으로, 행렬 X와 벡터 y를 만든 상태에서, (X'X)^-1에 X'Y를 곱하여 θ를 구합니다. <br> 여기서 잠시, 여기서 잠시 이 식의 의미를 이해하고, 어떻게 구현하는지 알려주고자 합니다. <br> 그렇다면, 명확하게, (X'X)^-1은 무엇일까요? (X'X)^-1는 X'X의 역행렬입니다. <br> 구체적으로, A를 X'X로 정의하면, X'는 행렬이고, X'X도 행렬입니다. <br> 그래서 A는 행렬 A라 하겠습니다. <br> 그러면, (X'X)^-1는 행렬 A를 역행렬로 바꾼 것입니다. <br> 알겠죠? 이 것은 A^-1이라 하겠습니다. <br>
<br>

이게 바로 계산하는 방법입니다. <br> X'X를 계산하고나서 그것을 역행렬로 바꿉니다. <br> 아직 Octave에 대해서는 다루지 않았지만, 뒤의 비디오에서 다룰 것입니다. <br> Octave 혹은 비슷한 프로그래밍 언어인 matlab에서는 아래의 명령어로 (X transpose X)의 역행렬에 X transpose와 y를 곱합니다. <br> Octave에서 X'는 X의 transpose를 나타내는 기호입니다. <br> 그리고, 붉은색 박스안에 있는 식은 X'에 X를 곱한 값을 계산합니다. <br> pinv는 행렬의 역행렬을 계산하는 함수입니다. <br> 그래서 이 식은 X'X의 역행렬을 계산하고, 그리고나서, X‘와 먼저 곱한 다음, y와 곱합니다. <br> 이상으로 이 식의 계산이 끝났습니다. <br> 

-  normal equation의 단점과 gradient descent의 장점 <br> 
gradient descent는 feature가 많을 때, 효과적입니다. <br> 만약, 수백만개의 feature를 가지고 gradient descent를 한다면, 효율적이고, 적당하게 돌아갈 것입니다. <br> 반대로 normal equation은 파라미터 θ를 구하기 위해, 이 식을 풀어야 합나다. <br> X'X의 역행렬식을 계산해야 합니다. <br> 이 행렬 X'X은 n개의 feature를 가지고 있다면, (n x n)행렬입니다. <br> 왜냐하면, X'의 차원수와 X의 차원수를 가지고 알 수 있는데, 이 둘을 곱하면 그 결과의 차원이 얼마인지 알 수 있고, 결국, 행렬 X'X는 (n x n) 행렬이 됩니다. <br> n은 feature의 개수입니다. <br> 그리고, 행렬의 역행렬을 계산하는데 걸리는 시간은, 대략 행렬의 차원수의 세제곱만큼 증가합니다. <br> 즉, 역행렬 계산의 걸리는 시간은 보통 세제곱만큼 걸립니다. <br> 가끔 세제곱보다 빠를때도 있지만, 차이는 거의 없습니다. <br> 결국, feature의 수 n이 엄청 커지면,
13:37
식의 계산속도는 느려질수 있고, normal equation은 결국 훨씬 더 느려집니다. <br> 그래서 n이 엄청 클 때에는, 저는 주로 gradient descent를 씁니다. <br> 왜냐하면 gradient descent는 세제곱만큼 시간이 들지 않기 때문입니다. <br> 만약 n이 작다면, normal equation이 파라미터를 구하는데 더 나을것입니다. <br> 그럼 언제 작고 언제 크다고 볼 수 있을까요? n이 100단위라면, (100 x 100)행렬의 역행렬을 구하는 것은 요즘의 컴퓨터수준으로 아무 문제가 없습니다. <br> n이 1000이라도, 저는 여전히 normal equation을 사용할 것입니다. <br> 1000 x 1000 행렬의 역행렬도 요즘 수준의 컴퓨터로 충분히 빠르게 구할 수 있습니다. <br> 하지만 만약 n이 10000이라면, 한번 생각해봐야합니다. <br> 10000 x 10000행렬부터 역행렬을 구하는 게 느려지기 시작합니다. <br> gradient descent로 갈아탈지 말지 고민하게 되지만, 아직은 아닙니다. <br> n이 1만이라면, 10000 x 10000 행렬은 계산 할 수는 있습니다. <br> 하지만, 이보다 더 큰 경우에는, gradient descent를 사용하는게 낫습니다. <br> 결국은, n이 10^6, 즉 feature가 백만개라면, (100만 x 100만) 행렬의 역행렬은 많은 시간이 필요합니다. <br> feature가 많다면, gradient descent를 강력하게 추천합니다. <br> 정확히 feature가 몇 개 일 때, gradient descent를 해야하는지, 정확한 숫자는 제시하기 어렵습니다. <br> 하지만, 저같은 경우, 1만개 정도 일 때, gradient descent나, 아니면, 뒤에서 배울 다른 알고리즘을 고려해봅니다. <br> 
<br>

 정리하자면, feature의 수가 많지 않을 때는, normal equation이 파라미터 θ를 구하는데, 좋은 방법입니다. <br> 정확히는 feature의 수가 1000보다 작을 때 normal equation을 gradient descent가 아닌 normal equation을 사용할 것입니다. <br> <br>
나중에 배울 내용에 대해서 살짝 이야기하자면, 더 복잡한 알고리즘을 배울 때 예를들면, 분류(classification) 알고리즘 중에서도 logistic regression 알고리즘 같은, 나중에 실제로 배울 테지만 사실 그런 정교한 학습 알고리즘에 normal equation은 적합하지 않지만, gradient descent는 적합합니다. <br> 그래서, gradient descent는 알고있으면 매우 유용한 알고리즘입니다. <br> 선형 회귀는 매우 많은 feature를 가지는 경우가 많고, 이 수업에서 배우는 gradient descent 외 알고리즘들은 예로 normal equation은 적용하기도 어렵습니다. <br> 하지만, 선형 회귀의 특정 모델에 대해서는 normal equation이
 <br>
gradient descent보다 더 빠를 수도 있습니다. <br>결국, 알고리즘이 어떠냐에 따라, 문제가 어떻고 feature가 얼마나 많냐에 따라 달라지기 때문에, 두 알고리즘은 알아두면 좋습니다. <br>
<br>

## Normal Equation Noninvertibility
- noramal equation과 역행렬이 없는 경우

게다가 octave에서 구현할 때는, pinv가 있습니다. <br> pinv 함수는 pseudo-inverse함수입니다. <br> 만약 다른 선형대수학 라이브러리를 사용한다면 pseudo-inverse라 불리는 것을 사용하면 됩니다. <br> 어찌됫든 pinv는 X'X의 역행렬이 없더라도, 올바르게 계산을 해줍니다. <br> 사실 그런 경우가 거의 일어나지 않기 때문에 선형회귀 구현에서 크게 문제가 되지는 않을 것입니다. <br>








