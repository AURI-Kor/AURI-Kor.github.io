---
layout: post
read_time: true
show_date: true
title: "INGV - Volcanic Eruption Prediction Report"
date: 2023-01-11
img: forpost/volcano.jpg
tags: [machine learning, report, data analysis]
author: Taewon Kim
description: "INGV - Volcanic Eruption Prediction Report"
---

# INGV - Volcanic Eruption Prediction 

## Volcanic Eruption Prediction Data
https://www.kaggle.com/competitions/predict-volcanic-eruptions-ingv-oe


## Purpose & Contents
과학자들은 지진 신호에 의한 화산 떨림을 조사함으로써 분화 시간을 확인한다. 일부 화산에서는 화산이 폭발하기 전 이 현상이 심화된다. 데이터 분석을 통해 다름 화산이 언제 폭발할지 예측할 수 있다. 활화산에 배치된 센서에 의해 수집된 데이터 센스를 분석하고 화산 분출 직전의 지진 파형을 식별한다.

- 데이터에서 주어진 신호기의 파형확인
- 분출까지의 시간 시각화 (by histogram)
- 분출까지의 시간 시각화 (by line)
- Test data set에서의 신호기 데이터 누락

## Conclusion
* 데이터에서 주어진 신호기의 파형 확인
  <figure>
    <img src="/assets/img/in_post/vol/vol_1.png" title="wave">    
    <figcaption>신호기 파형1</figcaption>
</figure>

누락된 신호를 0으로 가정하면 아래와 같다.
<figure>
    <img src="/assets/img/in_post/vol/vol_2.png" title="wave">    
    <figcaption>신호기 파형2</figcaption>
</figure>
     

* 분출까지의 시간 시각화 (by histogram)
  
 <figure>
    <img src="/assets/img/in_post/vol/vol_3.png" title="hist">    
    <figcaption>Time to Eruption 1</figcaption>
</figure>
 <figure>
    <img src="/assets/img/in_post/vol/vol_4.png" title="line">    
    <figcaption>Time to Eruption 2</figcaption>
</figure>
* Test data set에서의 신호기 데이터 누락
  
  <figure>
    <img src="./starwars/vol_5.png" title="Miss">    
    <figcaption>Missed data on test set</figcaption>
    </figure>
  ## Code
  
  센서 3번, 센서 2번, 센서 8번, 센서 5번에서의 신호 누락이 두드러진다.


{% include_relative IPY/volcano.html %}