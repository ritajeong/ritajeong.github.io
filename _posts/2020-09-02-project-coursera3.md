---
layout: post
title: "Coursera Machine Learning Study Week3"
subtitle: ""
categories: project
tags: project
comments: true
date: 2020-09-02 20:13:00 -0400
---


# Classification and Representation
## Classification
- 학습목표 : 우선은 0과 1 두 가지의 값만을 갖는 분류 문제를 먼저 다루도록 하고 이후에 0, 1, 2, 3 등 여러가지 y 값을 찾는 분류 문제도 다룰 수 있도록 하겠습니다.
이와 같은 문제를 다중분류 (multiclass classification) 문제라고 하죠.
 
 - 선형 회귀를 분류 문제에 적용하는 건 대부분의 경우에서 좋은 생각이 아닙니다.    
 이 첫번째 예시에서, 제가 데이터를 추가하기 이전의 선형 회귀는 운좋게 우리에게 특정 예시들에 대해 잘 작동하는 가설을 주었지만 일반적으로 선형회귀를 (분류) 데이터에 적용하면, 운이 좋을 수도 있지만 대부분은 잘못될 것입니다.   
 그래서 저라면 분류 문제들에 대해 선형 회귀를 사용하지 않을 겁니다. 

- 앞으로의 강의에서는 로지스틱 회귀라 불리는 알고리즘을 공부할 건데요, 로지스틱 회귀의 결과값, 예측값은 항상 0에서 1사이이며 1보다 크거나 0보다 작은 값을 가질 수 없습니다.   


## Hypothesis Representation
- 학습목표 : 로지스틱 회귀분석을 시작하면서 여러분들에게 표현 모델을 보여주고 싶습니다. 그것은, 우리가 분류문제를 가지고 있을 때에 우리의 가설을 표현하기 위해 사용할 함수입니다.    

- 이전에, 우리는 분류문제의 결과값이 0에서 1 사이가 되도록 한다고 말했습니다.     그래서 우리는 이러한 결과값을 만족하는가설 즉, 예측값이 0에서 1사이인 가설을 만들고 싶습니다. 선형 회귀분석을 사용할 때에는, 이것이 가설 형식이었습니다. h(x)가 Θ의 전치행렬 * x입니다. 로지스틱 회귀분석에서는, 전 이것을 조금 변경하여 g(Θ의 전치행렬 * x)으로 다음과 같은 g함수를 사용하여 변경합니다. G(z) 중, z는 실수이며, 1 더하기 -z 지수의 e 분의 1로 정합니다.

- 이것은 시그모이드 함수 혹은 로지스틱 함수이며 로지스틱 함수라는 용어는 로지스틱 회귀분석이라는 이름의 만들었습니다. 이 외에도, 시그모이드라는 용어나 로지스틱 함수라는 용어는 기본적으로 동의어이며 같은 뜻을 의미합니다. 

## Decision Boundary
- 학습목표 :  we talked about the hypothesis representation for logistic regression.
we know that y equals one is more likely, that is the probability that y equals one is greater than or equal to 0.5, whenever theta transpose x is greater than zero. And this formula that I just underlined, -3 + x1 + x2, is, of course, theta transpose x when theta is equal to this value of the parameters that we just chose.
- 선형경계가 생기는 경우와 그렇지 않은 경우가 존재한다. 
decision boundeary / non-linear decision boundaries.
So, with these visualizations, I hope that gives you a sense of what's the range of hypothesis functions we can represent using the representation that we have for logistic regression.

# Losixtic Regression Model
## Cost Function
- 학습 목표 : 로지스틱 회귀(logistic regression)에서 매개변수 θ를 어떻게 fitting하는지 알아보도록 하죠. 특히, 매개변수 θ를 fitting하기 위해서 우리가 최적화할 목표물, 즉 비용함수가 무엇인지 정의하려고 합니다.
- 이 비용 함수는 선형 회귀를 다룰 때에는 문제가 없었어요. 그치만, 우리가 지금 하고 있는 건 로지스틱 회귀입니다. 만약 여기에 J를 대입하고, 이 비용 함수를 최소화할 수 있다면 그럼 문제가 없을 거예요. 하지만 우리가 여기 이 비용 함수를 사용한다면 이 비용 함수는 매개변수 θ에 대해 볼록 함수가 아니라고 밝혀졌어요. 볼록 함수가 아니라고 한 게 무슨 뜻이냐면, 우리에게 어떤 비용함수 J(θ)가 있어서 로지스틱 회귀 문제를 다룰 때 이 함수 h가 비선형성을 가져서, 즉, 1/(1+e^(-θT)x)가 됩니다. 즉 이건 꽤 복잡한 비선형 함수입니다. 그리고 이 sigmoid함수를 다시 이 안에 대입하고, 또 이 비용 함수를 여기에 대입한다면 J(θ)는 이런 모양이 됩니다. 여기 보이는 바와 같이 J(θ)는 이렇게 많은 극소점을 가진 함수가 되지요. 이런 함수를 수학적 용어로 비볼록함수라고 합니다. 그리고 이런 비볼록함수의 경우 경사하강법을 적용해도 전체 함수의 최소값에 도달한다는 보장이 없습니다. 반면에 비용함수 J(θ)가 볼록함수라고 한다면 이 함수는 활 모양으로 한 번만 구부러진 함수이고, θ에 대해 경사하강법을 적용함으로서 수렴되는 값은 반드시 전체 함수의 최소값이라고 할 수 있습니다. 그러므로 이 제곱된 비용 함수를 사용함으로 인해 생기는 문제점은 이 가운데 있는 게 비선형적인 함수이기 때문에 J(θ)가 비볼록함수가 된다는 겁니다. 
 - 그래서 우리가 하고 싶은 건, 다른 비용 함수를 제시하는 겁니다. 볼록한 비용 함수를요. 그래서 경사하강법 같은 좋은 알고리즘을 적용할 수 있도록 하고, 전체 함수의 최소값을 찾을 수 있도록 하는 거죠. 
- 이제 로지스틱 회귀에서 사용할 비용함수를 살펴보겠습니다.우리가 이야기할 것은 비용, 즉 알고리즘이 지불해야 할 값에 대한 겁니다. 알고리즘이 hθ(x)값을 넘어섰을 때요. 그래서 예를 들어 이게 0.7같은 숫자라면, 그건 hθ(x)값을 예측하고 있습니다. 그리고 실제 비용을 가리키는 레이블은 y가 됩니다. 이 비용은 y=1일 때 -log(hθ(x))이고요, y=0일 때 -log(1-hθ(x))입니다. 이거 좀 복잡해 보이죠? 하지만 이 함수를 그리면서 이게 뭘 하는지 직감적으로 알아봅시다. 먼저 y=1일 때 입니다. 만약 y=1이라면, 비용함수는 -log(hθ(x))입니다. 이걸 플롯해보면, 여기 x축을 h(x)라고 합시다. 그러면 우리가 알고 있는 대로 가설 h(x)는 0 아니면 1이잖아요, 맞죠, 그래서 h(x)는 0에서 1까지만 값을 가집니다. 이 비용함수가 어떻게 생겼는지 플롯해 보면 이렇게 된다는 걸 알 수 있어요.
 플러스마이너스를 뒤집으면 이게 -log(z)예요. 그리고 우리가 알고 싶은 건 이 함수 중에서 0과 1 사이가 어떻게 생겼는지이므로, 나머지를 지웁시다. 그러면 남은 게, 이제 알겠죠. 이 부분의 곡선이에요. 그리고 이게 바로 여기 왼쪽의 곡선입니다. 이제 이 비용함수는 몇 가지 재미있고 바람직한 속성을 가지고 있어요. 첫째로, 잘 보면 y=1인 경우 h(x)=1이 됩니다. 다시 말하면, 가설을 정확하계 예측한 경우 h=1이고 y가 가설이 예측한 값과 맞아떨어진다면 비용은 0이 됩니다. 맞죠? 이건 곡선이 평평해지지 않는다는 사실과 부합합니다. 커브는 계속 꺾어지게 됩니다. 다시 해 보죠, h(x)=1일 경우에 주목한다면 이 가설은 y=1일 것을 예측하고, 실제로 y=1이라면 비용은 0이 됩니다. 그건 바로 여기 이 점에 해당합니다. 맞죠? 만약 h(x)=1이라면 우리가 생각할 수 있는 y=1인 경우는 여기 한군데입니다. 그런데 만약에 h(x)=1이고 비용이 여기라면 이건 0가 됩니다. 그리고 이건 우리가 원하던 건데요, 왜냐하면 우리가 결과값 y를 정확히 예측했다면 비용은 0이기 때문이죠. 하지만 여기서 하나 더 알게 된 점은, 여기 h(x)가 0에 가까워지면 그래서 가설의 출력값이 0에 가까워지면, 비용은 증대하고 무한대로 가 버린다는 겁니다. 그리고 이게 무슨 역할을 하냐면, 가설 hθ(x)=0, 즉 y=1일 확률이 0일 때를 직관적으로 포착하게 해 줍니다.

- 예시로 이해하기
예를 들어 당신은 의사이고 환자에게 이렇게 말했습니다. "당신이 악성 종양을 가지고 있을 확률, 즉 y=1일 확률은 0입니다." "그래서 당신의 종양이 악성이라는 건 절대적으로 불가능해요."하지만 이런 경우도 있죠. 검사를 해 보니 그 종양, 그 환자의 종양이 악성이었습니다. 그래서 만약 y=1이라면, 벌써 환자에게 말했는데, '악성일 확률은 0이에요' 하고. '그래서 악성 종양이라는 건 불가능해요' 하고 말했는데, 만약 우리가 환자에게 그렇게 확신을 가지고 말했는데 결국엔 틀렸다면 이 학습 알고리즘을 처벌해야 하죠. 엄청난 비용을 부과시켜야 해요. 그게 여기에 포착된 비용의 값입니다. 만약에라도 y=1이라는 값이 나오면 비용은 무한대이고 h(x)=0이 됩니다. 

## Simplified Cost Function and Gradient Descent
- 학습목표
1. 지금까지 사용해 왔던 비용 함수를 조금 더 간단하게 쓰는 방법을 알아보겠습니다. 
2. 그리고 또 어떻게 경사하강법을 적용해서 로지스틱 회귀의 매개변수를 피팅할건지도 알아볼 겁니다. 
3. 이 강의의 마지막에서 여러분은 로지스틱 회귀가 완벽하게 작동하는 버젼을 어떻게 구현하는지를 알게 될 겁니다.
- y가 0이나 1의 값이기 때문에 우리는 비용 함수를 작성하는 더 간단한 방법을 생각할 수 있습니다. 특히, 비용 함수를 여기의 두 줄처럼 y=1 또는 y=0이라는 두가지 케이스로 나누어서 적는 대신에 저는 이 두 줄을 하나의 방정식으로 압축하는 방법을 보여드리겠습니다. 그리고 이것은 비용 함수를 작성하고 기울기 강하를 유도하는 것이 더 편리 할 것입니다. 구체적으로 다음과 같이 비용 함수를 쓸 수있습니다. 저는 이제 cost(h(x), y)를 -y*log(h(x)) -(1-y)* log(1-h(x))라고 적겠습니다. 간단하게 설명하자면 이 표현은, 아니,이 식은 우리가 위에 적은 비용함수의 정의와 동일하며 함축된 방법입니다. 
- 다시 한번 말씀드리자면, 제 hypothesis의 결과를 입력 x와 매개 변수 θ가 주어졌을 때 y가 1과 같을 확률로 해석할 것입니다. 하지만, 당신은 y가 1과 같을 확률을 추정하는 것을 단지 나의 가설이라고만 생각할 수 있습니다. 그래서 우리가 해야 할 것은 우리의 training set에 최적하기 위한 매개 변수인 θ의 함수인 J(θ)를 어떻게 최소화 할 것인가 입니다. 우리는 비용 함수를 최소화하기 위해서 경사 하강법을 사용할 것 입니다.
- 경사 하강법으로 로지스틱 회귀를 구현할 때, 우리는 θ0부터 θn까지 모두 다른 매개 변수 값을 가지고 있으며, 이 식을 이용해서 θ를 업데이트 해야 합니다. 우리가 할 수 있는 한가지는 for loop입니다. i=0부터 n까지나, i=1부터 (n+1)까지 for loop를 사용해서 우리는 이 각각의 매개 변수들을 업데이트 해야합니다. 물론 for 루프를 사용하는 것이 아니라, vector rise implementation을 사용하는 것이 이상적입니다. vector rise implementation은 m+1개의 매개 변수를 한번에 업데이트할 수 있습니다. 여러분이 스스로 이해했는지 확인하기 위해서, vector rise implementation을 이 알고리즘에 수행하는 방법을 확인할 수 있습니다. 
- 로지스틱 회귀를 위한 하강 기울기 알고리즘에 대해 알게 되었습니다. 우리가 이전 선형 회귀에 사용된 마지막 아이디어는 feature scaling입니다. 우리는 feature scaling이 어떻게 선형 회귀의 경사 하강법을 빠르게 수렴하게 했는지 봤습니다. 선형 회귀입니다. feature scaling의 아이디어를 로지스틱 회귀의 경사 하강법에도 적용해 보겠습니다. 로지스틱 회귀입니다. 우리는 매우 다른 범위를 가지는 feature들을 가지고 있다면, feature scaling을 적용하여 로지스틱 회귀에서 경사 하강법을 빠르게 만들어 보겠습니다.
## Advanced Optimization
- 학습목표 : we talked about gradient descent for minimizing the cost function J of theta for logistic regression. I'd like to tell you about some advanced optimization algorithms and some advanced optimization concepts.
- So another way of thinking about gradient descent is that we need to supply code to compute J of theta and these derivatives, and then these get plugged into gradient descents, which can then try to minimize the function for us. 
- But gradient descent isn't the only algorithm we can use. And there are other algorithms, more advanced, more sophisticated ones, that, if we only provide them a way to compute these two things, then these are different approaches to optimize the cost function for us. So conjugate gradient BFGS and L-BFGS are examples of more sophisticated optimization algorithms that need a way to compute J of theta, and need a way to compute the derivatives, and can then use more sophisticated strategies than gradient descent to minimize the cost function.
- 장점 : No need to manually pick alpha. Often faster than gradient descent.
- 단점 : More complex.
- 다른 알고리즘들은 직접 구현하기보다 라이브러리를 사용하는 것을 추천. 

## Multiclass Classification: One-vs-all 
- 학습목표 : 멀티클래스 분류 문제에 대해 로지스틱 회귀를 어떻게 적용하는지,  특히 'one-vs-all'분류라고 불리는 알고리즘에 대해 배운다.   
- 
