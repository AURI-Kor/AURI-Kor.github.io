---
layout: post
read_time: true
show_date: true
title: "ML summary - simple regression"
date: 2021-03-24
img: forpost/2.jfif
tags: [machine learning, study_theory, linear regression]
author: Taewon Kim
description: "ML summary - simple regression"
---


Simple Regression
=======================

> AURIWALL

Linear Regression
------
직선식 형태의 회귀 방법 
기계학습이란 예측을 하기 위해서 주어지는 Data Item (과거 데이터)에 의한 예측(출력)

    supervised Learning
    예측 모델에서 어떤 과거의 데이터를 통해 새로운 상황에 대한 예측을 만들어내는 방법
    * Clustering 

    unsupervised Learning
    과거의 데이터를 바탕으로 하지 않는 방식

### Notation
    m = Number Of training examples
    x's = input variable / features
    y's = output variable / target variable

Training Set -> Learning Algorithm ->  **h** (Estimated)

## Cost function
 Hypothesis : $$h_{\theta}(x) = \theta_{0} + \theta_{1}x \\ \theta_{i}'s : parameters$$

Idea : 각각의 theta 를 선정해 h(x)의 값이 training set (x, y)의 y와 가장 근접하도록 하는 것 (MAE, MSE) Squared error function

Hypothesis: $$h_{\theta}(x) = \theta_{0} + \theta_{1}x$$
Parameters : $$\theta_{0} , \theta_{1}$$
Cost function :
$$J(\theta_{0}, \theta_{1}) = {1\over2m}\Sigma_{i=1}^{m}(h_{\theta}x^{i} - y^{i})^{2} $$

Goal : $$ minimize _{\theta_{0}, \theta_{1}} J(\theta_{0}, \theta_{1})$$

이를 단순하게 표현하면
 
Hypothesis: $$h_{\theta}(x) = \theta_{1}x$$
Parameters : $$\theta_{1}$$
Cost function :
$$J(\theta_{1}) = {1\over2m}\Sigma_{i=1}^{m}(h_{\theta}x^{i} - y^{i})^{2} $$

Goal : $$ minimize _{\theta_{1}} J(\theta_{1})$$

## Gradient descent
$$ J(\theta_{1}, \theta_{1})$$ 
에 대해 우리가 원하는 것은 이의 최솟값을 찾는 것이다.
$$ minimize _{\theta_{0}, \theta_{1}} J(\theta_{0}, \theta_{1})$$
하지만 계속 변화하는 $$ \theta_{1}, \theta_{1}$$ 에 대해서 우리는 여러 개의 minimum value들을 가질 수 있고 이를 복수형의 minima로 표현한다.

이러한 minima들은 $$ \theta_{1}, \theta_{1}$$ 값의 변화에 따라 국소적인 최소값들을 가지며 이를 Local minima라고 한다.

* 어떤 수식에 대해 J는 기울기 값을 가지는데 이를 수정하기 위해 Learning rate가 사용된다.

