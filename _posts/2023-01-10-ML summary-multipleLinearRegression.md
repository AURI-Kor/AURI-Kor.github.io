---
layout: post
read_time: true
show_date: true
title: "ML summary - Multiple Variable Linear regression"
date: 2021-03-24
img: forpost/2.jfif
tags: [machine learning, study_theory, Decision Tree]
author: Taewon Kim
description: "ML summary - Multiple Variable Linear regression"
---

# Multiple  Variable Regression

feature = dimension= attribute

### Notation
$$ n = number of features\\x^{i}  = input(features) of i_{th} training example \\ x_{j}^{i} = value if features j in i_{th} training example\\ $$

기본적으로 linear Regression 상의 모든 벡터는 comlumn vector로 나타내며 필요한 경우  row vector를 통해 나타내게 된다.


Hypothesis: $$h_{\theta}(x) = \theta_{0} + \theta_{1}x$$

이전의 식으로부터 새로운 가설을 이끌어 낼 수 있다.

Hypothesis: $$h_{\theta}(x) = \theta_{0} + \theta_{1}x_{1} + ... + \theta_{n}x_{n}$$

위와 같이 모델을 simple하게 확장할 수 있으며 각각의 벡터의 column vector를 통해 좀 더 손쉽게 나타낼 수 있다.

$$ x = \begin{bmatrix} x_{0} \\ x_{1} \\ ... \\ x_{n}\end{bmatrix} \in R^{n+1} \quad \theta = \begin{bmatrix} \theta_{0} \\ \theta_{1} \\ ... \\ \theta_{n}\end{bmatrix} \in R^{n+1} \\ 
\theta^{T} x = h_\theta(x) = \theta_{0} + \theta_{1}x_{1} + ... + \theta_{n}x_{n}$$

## Feature Scailing

Idea : Make Sure features are on a similar scale

E.g. 집의 가격을 결정하는 요인에 대해서 생각해보자.

x1 = size (0~2000 feet^2)

x2 = number of bedrooms (1~5)

두 feature를 별개의 요소이다. 두 개의 요소가 모두 엇비슷하게 영향을 미친다고 가정한다면 x1은 최대 2000의 값을 가지고 계수 값도 그만큼 클 것이다. 두 features가 가지는 가중치 값이 상이하게 되고, 이를 randomize하게 학습하게 되면 x1의 변화값이 크기 때문에 계수값에 대해서 모델의 예측치의 변화폭이 커지게 된다.

x1의 변화폭이 10인 것에 비해 x2의 변화폭이 1000이라 가정한다면, x1의 변화폭이 큰 영향을 미치지 않는 것에 비해 x2의 변화폭은 큰 영향을 미치게 된다. 따라서 가중치(계수값)을 비슷하게 만들어 주기 위해 두 feature의 요소 값의 범위를 비슷하게 만들어주는 것이 필요하다. (nomalization) 

* 학습 시간을 단축시켜주는 장점도 있다.

Feature scailing은 최대값만 고려하는 방법도 있으며 최소값을 함께 고려하는 방법이 있다. 

최소값을 고려하는 방식에서는 실제값에서 최소값을 뺀 값을 최대값과 최소값을 뺀 값으로 나누어 준다.

### Mean Normalization
Replace xi with xi - mi to make features  have approximately zero mean.

E.g.

$$ x_{1} = {size-1000\over 2000} \\ x_{2} = {\#bedrooms -2 \over 5} \\$$
$$ -0.5 \le x_{1} \le0.5 \quad\&\quad -0.5 \le x_{2} \le0.5 $$

아래와 같은 예제가 있다고 가정을 하자, 데이터의 범위가 18~55라고 하면, 이를 nomalization을 했을 때, -1에서 1사이의 값에 데이터 값들이 적절하게 분배될 것이다.

$$ Mean(\mu) : 30 \\ Variance(\sigma) : 10^{2} $$

하지만 만약 outlier로 3000의 값을 가지는 데이터가 존재한다고 가정한다면 1의 값에 3000에 해당하는 데이터가 배정되도 나머지 18~55의 값을 가지는 데이터는 한없이 -1에 가까운 위치로만 배정이 될 것이다. max와 min에 가까운 몇 개의 outlier들이 기준이 된다면 이와 같은 문제가 발생한다. 따라서 outlier로 인해 데이터들이 -1에만 치중되는 결과를 피하기 위해 standard nomalization을 할 수 있다. standard nomalization은 몇 개의 기준은 아주 방대한 양의 데이터 일부로 전락하게 하기 때문에 주로 사용된다.


## Gradient Descent
$$ x = \begin{bmatrix} x_{0} \\ x_{1} \\ ... \\ x_{n}\end{bmatrix} \in R^{n+1} \quad \theta = \begin{bmatrix} \theta_{0} \\ \theta_{1} \\ ... \\ \theta_{n}\end{bmatrix} \in R^{n+1} \\ 
\theta^{T} x = h_\theta(x) = \theta_{0} + \theta_{1}x_{1} + ... + \theta_{n}x_{n}$$

### Previous

$$ {\partial \over \partial \theta_{j}} J(\theta_{0}, \theta_{1}) = ...\\
j = 0 : \quad{\partial \over \partial \theta_{0}} J(\theta_{0}, \theta_{1}) = {1 \over m}\Sigma_{i=1}^{m}(h_{\theta(x^{i}) - y^i}) \\
j = 1 : \quad{\partial \over \partial \theta_{1}} J(\theta_{0}, \theta_{1}) = {1 \over m}\Sigma_{i=1}^{m}(h_{\theta(x^{i}) - y^i})* x^i $$


### In polynomial 
 x1　=  1　3
 
 x2　=  2　-1
  
 y　 =  5　7

 
$$ {\partial \over \partial \theta_{j}} J(\theta_{0}, \theta_{1}, ...) = ...\\
\theta_{j} := \theta_{j} - \alpha{1 \over m} \Sigma_{i=1}^{m}(h_{\theta(x^{i}) - y^i})* x_j^i \\
j = 0 : \quad {\partial \over \partial \theta_{0}} J(\theta_{0}, \theta_{1}, \theta_{2}) =\theta_0 - \alpha{1 \over m}\Sigma_{i=1}^{m}(h_{\theta(x^{i}) - y^i})*x_0^i \\
j = 1 : \quad{\partial \over \partial \theta_{1}} J(\theta_{0}, \theta_{1}, \theta_{2}) = \theta_0 - \alpha{1 \over m}\Sigma_{i=1}^{m}(h_{\theta(x^{i}) - y^i})* x_1^i \\
j = 2 : \quad{\partial \over \partial \theta_{2}} J(\theta_{0}, \theta_{1}, \theta_{2}) = \theta_0 - \alpha{1 \over m}\Sigma_{i=1}^{m}(h_{\theta(x^{i}) - y^i})* x_2^i $$

## Polynomial Regression

Linear Regression에서는 완벽히 비례적인 데이터에 대해서만 훌륭하게 작동할 것이다. 집값 예측을 위한 Linear Regression이 존재한다면 집의 면적에 비례적으로 각 평수에 평당 가격 정도를 곱하는 정도의 예측밖에는 하지 못하게 된다. 따라서 선형적인 분류를 따르지 않는 데이터를 분석하기 위해 다른 모델이 필요하다.

E.g.

$$ 
\theta_0 + \theta_1 x + \theta_2  {x}^2 \\
\theta_0 + \theta_1 x + \theta_2  \sqrt{x} \\
\theta_0 + \theta_1 x + \theta_2  x^2 + \theta x^3
$$

root 가 들어간 Linear Regression 문제를 풀기 위해서는 x의 root에 해당하는 columns 을 추가한다.

$$
 x1　=  1　\quad 2　\quad 4\\ 
 \sqrt{x}　=  1　\quad \sqrt 2　\quad 2\\ 
 y　 =  4　\quad 7　\quad 9

$$

위에서의 식과 동일하게 x2의 자리에 x1의 root에 해당하는 값을 이용하면 root가 포함된 polynomial Regression의 Gradient Descent를 구할 수 있다.

## Office hour

### 머신러닝 vs 딥러닝
과거에는 컴퓨팅 자원의문제로 딥러닝이 불가능했다. 주로 저장장치, GPU의 한계로 인해 딥러닝에 필요한 자원의 필요를 만족시키는게 어려웠다. Dataset의 미비도 딥러닝이 어려웠던 이유로 알려져 있다. 현재는 많은 개방형 데이터들이 존재하고 이와 같은 많은 데이터와 과거와 비교해 충분히 휼륭해진 컴픁 자원을 통한 연산으로 딥러닝을 수행하는 것이 가능해졌다.


머신러닝의 이슈는 주어진 한정된양의 데이터를 통해 수학적인 수식을 통해 원하는 바를 얻어낼 수 있을까에 관란 것이었다. 이에 비해 딥러닝은 엄청난 수의 데이터 학습을 통해 결과를 도출해 내는 것이기 때문에 현재 머신러닝의 학습 효율은 딥러닝만큼 좋게 나타나지는 않고 있다. 그렇다면 머신러닝을 해야하는 이유는 무엇인가. 딥러닝 모델 디자인에서 좋은 학습을 위해서는  variant 조정과 같은 trick들이 필요하다. 이는 결국 머신러닝에서 시작된 수학적 수식에서 비롯된다. 간단한 예로 어떻게 variant를 줄이는가에 대해 loss function을 적용하는 방법이 있을 것이다.

