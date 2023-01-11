---
layout: post
read_time: true
show_date: true
title: "ML summary - logistic regression"
date: 2023-01-11
img: forpost/4.jfif
tags: [machine learning, study_theory, logistic regression]
author: Taewon Kim
description: "ML summary - logistic regression"
---


Logistic Regression
===

예측 값이 연속적인 값을 가지지 않는 분류 문제를 binary classification이라고 한다. 이는 class가 2종류인 분류 문제이며, 대표적으로는 스팸 메일 분류가 있다. 이러한 문제를 푸는 방법 중 하나로 Logistic Regression이 있다.

E.g
- Email : Spam / Not Spam
- Online Transactions : Fraudulent (Yes / No)
-Tumor : Malignant / Benign

$$ y \in \{ 0, 1 \}$$

<figure>
    <img src="./logistic/lo1.png" title="binary classification">    
    <figcaption>binary classification for tumors</figcaption>
</figure>

$$ if h_\theta(x) \ge 0.5, \quad predict  \quad y = 1\\ if h_\theta(x) \le 0.5, \quad predict  \quad y = 0  $$

target variable이 0 또는 1로 표현이 된다면 위와 같은 linear regression을 사용할 수도 있다. 모델은 예측과 관찰의 error가 최소치가 되도록 설계해야 한다.

<figure>
    <img src="./logistic/lo2.png" title="outlier classification">    
    <figcaption>result of outlier</figcaption>
</figure>

Training data가 위와는 다르게 종양의 크기가 극명하게 큰 환자가 있다고 가정하자. linear regression은 x의 값이 커지면 커질수록 y값도 극명하게 커지게 된다. 만약 이렇게 된다면 이 환자의 y값은 여전히 1이지만 실제 분류선에서의 y값의 크기는 커지게 될 것이다.

이는 에러값의 증가를 불러오고 좀 더 완만한 경사도를 지닌 linear model을 만들어내게 된다. 기존에 3.6를 기준으로 악성과 양성을 구분하던 모델은 기준점을 높이게 될 것이다. 결론적으로 잘못된 분류 모델을 만들어 낼 수 있다.

선형식으로 이를 해결할 수 없기 때문에 우리는 Logistic regression을 도입할 수 있다.
<figure>
    <img src="./logistic/lo3.png" title="logistic classification">    
    <figcaption>logistic regression</figcaption>
</figure>

$$h_{\theta} (x) = g(\theta^{T} x) = {1 \over {1 + e^{-\theta^Ts}}} 

\\ e.g. :  y = ax + b 
\\ y = \sin (ax + b) $$

입력 features가 1개 이상일 때, 
$$h_{\theta} (x) = g(\theta_0 +\theta _1 x _1 +\theta _2 x _2 )$$

## decision boundary

정의된 classification model에 대해 target variable을 구분 짓는 선을 그릴 수 있다.
E.g.
$$if \quad -3+x_1 + x_2 \ge 0, \quad y = 1$$
<figure>
    <img src="./logistic/lo4.png" title="logistic classification">    
    <figcaption>Decision boundary</figcaption>
</figure>

## cost function

주어진 target variable에 대해 i번째 training data에 대해 이를 분류하는 model이 있다면 실제 label에 대한 loss를 계산할 수 있다. 만약 label 이 1인 data에 대해 1이라고 판단한다면 loss는 0일 것이고 이는 잘 분류했다고 볼 수 있다.

loss는 0에 가까울 수록 좋다고 볼 수 있다. 하지만 이같은 단순한 loss function은 사용되지 않는다. 이는 분류 확률을 고려하기 때문이다. 95%의 확률로 분류된 것과 55%의 확률로 분류된 것이 다르기 때문에 label을 정확히 예측할 수 있도록 분류 확률을 높이는 방식으로 loss를 설계할 필요가 있다.

<figure>
    <img src="./logistic/lo5.png" title="logistic classification">    
    <figcaption>cost function</figcaption>
</figure>

## Gradient descent in Logistic Regression

$$ J(\theta) = {-1 \over m}[\Sigma_{i=1}^m h_\theta(x^{(i)}) + (1-y^{(i)})\log(1 -  h_\theta(x^{(i)}))] $$

이를 최소화하는 것이 Gradient descent의 목적이다.

$$ J(a, b) = - \log _e {1 \over {1 + e^{-(ax+b)}}}
\\ {dJ(a, b) \over da } = {e^{-(ax+b)} \over 1 + e^{-(ax+b)}} x
$$

ax + b -> z로 치환하여 정리하면

$$ {dJ(a, b) \over da } = -{e^{-z}\over1+e^{-z}} = - (1 - {1 \over1+e^{-z}})$$

와 같은 형태로 정리할 수 있다.

## Multiclass classificaton

binary classification 보다 좀 더 세분화된 target label이 있을 때,
<figure>
    <img src="./logistic/lo6.png" title="logistic classification">    
    <figcaption>binary classification VS multiclass classification</figcaption>
</figure>

one or All(rest)
 --
각각의 class에 대해 대응하는 각각의 classification model을 반드는 모델. 여러 카테고리 중 하나만을 positive로 가정하여 학습하고 모든 i번째 카테고리에 대해 학습을 한다.

<figure>
    <img src="./logistic/lo7.png" title="logistic classification">    
    <figcaption>How to classify multiclass labels [One or All]</figcaption>
</figure>

 E.g. 
 $$ x_1 = 1, \quad x_2 = 2 \\
 \quad  2x_1 + 3x_2 +4 = 12 \quad about \quad 99.95\% \\
 \quad  -x_1 + 5x_2 - 3 = 6 \quad about \quad 98\% \\
 \quad  -4x_1 + 3_2 +22 = 0 \quad about \quad 5\% \\
 $$
 $$
 {e^{12} \over {e^{12} + e^6 + e^0}} = 92\% \\
 {e^{6} \over {e^{12} + e^6 + e^0}} = 7\% \\
 {e^{0} \over {e^{12} + e^6 + e^0}} = 1\% \\
 $$