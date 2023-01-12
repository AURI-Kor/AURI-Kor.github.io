---
layout: post
read_time: true
show_date: true
title: "Starwars Character Report"
date: 2023-01-11
img: forpost/starwars.jpg
tags: [machine learning, study_model, perceptron]
author: Taewon Kim
description: "Starwars Character Report"
---

# Starwars Character Report

## Starwars Data

Starwars API의 데이터는 스타워즈에 등장하는 캐릭터들의 특징을 정리해 놓은 데이터입니다.
* Data : https://dplyr.tidyverse.org/reference/starwars.html

## Purpose & Contents

해당 Report는 스타워즈 캐릭터의 특징에 대한 흥미에 의해 제작되었습니다. 분석 내용은 아래와 같습니다.

- 스타원즈 캐릭터 성별 비율
- 성별에 따른 캐릭터 신장의 분포
- 가장 무거운 캐릭터와 가장 가벼운 캐릭터
- 스타워즈 캐릭터의 키/몸무게의 상관관계 분석

## Data 
**columns**
* name: 캐릭터 이름 
* height: 키   
* mass: 몸무게  
* hair_color: 머리카락 색  
* skin_color: 피부색  
* eye_color: 눈동자 색  
* birth_year: 생년  
* sex: 생물학적 성별  
* gender: 사회적 성별  
* homeworld: 고향  
* species: 종

**Data Summary**
* 총 데이터 개수:  957  
* 총 결측치 수: 105 = 전체 데이터의 10.97%   
* 스타워즈에 등장하는 등장인물 수:  87  
* 스타워즈에 등장하는 종족 수:  37  

## Conclusion
* 스타워즈 캐릭터의 성별 비율
  <figure>
    <img src="/assets/img/in_post//starwars/sw_g1.png" title="sex">    
    <figcaption>Gender/Sex 비율</figcaption>
</figure>

     : 남성/남성 gender를 가진 캐릭터가 80% 가량을 차지하며, 로봇(Robot)과 자웅동체(hermaphoroditic)가 존재한다.

* 성별에 따른 캐릭터 신장의 분포
  
 <figure>
    <img src="/assets/img/in_post//starwars/sw_g2.png" title="Height">    
    <figcaption>Height distribution</figcaption>
</figure>
  : 남성 캐릭터의 키가 대체로 여성보다 크며, 로봇은 그보다 키가 작다.
* 가장 무거운 캐릭터와 가장 가벼운 캐릭터
<figure>
    <img src="/assets/img/in_post//starwars/sw_g3.png" title="High-weight">    
    <figcaption>High-weight races</figcaption>
</figure>

    :   몸무게 상위 10개 종족은 ['Hutt'], ['Kaleesh'], ['Wookiee'], ['Trandoshan'], ['Besalisk'], ['Neimodian'], ['Nautolan'], ['Mon Calamari'], ['Cerean'], ['pau'an'] 이다
<figure>
    <img src="/assets/img/in_post//starwars/sw_g4.png" title="Weight">    
    <figcaption>Weight Graph by Race</figcaption>
</figure>

    :  ['Ratts Tyerell']의 몸무게가 15.0 (으)로 가장 가볍다   
  
       ['Jabba Desilijic Tiure']의 몸무게가 1358.0 (으)로 가장 가볍다 

       - Hutt 캐릭터의 몸무게는 outlier로 보아 제외하였다 

* 스타워즈 캐릭터의 키와 몸무게는 상관관계
  
  <figure>
    <img src="./starwars/sw_g5.png" title="correlation">    
    <figcaption>Weight-Height correlation</figcaption>
    </figure>
  : 키와 몸무게는 일반적으로 상관관계를 가진다. 
  인간과 다른 행성에 사는 종족이지만, 키와 몸무게는 대체로 비례 관계를 보인다.

  ## Code

{% include_relative IPY/starwars.html %}