---
layout: post
read_time: true
show_date: true
title: "LAkers match Report"
date: 2023-01-11
img: forpost/LAkers.jpg
tags: [machine learning, data analysis, report]
author: Taewon Kim
description: "LAkers match Report"
---

<figure>
  <img src="/assets/img/in_post/LAkers/LAkers.jpg" title="I">    
  <figcaption></figcaption>
</figure>

## LAkers Data

LA Lakers는 NBA 서부 콘퍼런스 퍼시픽 디비전 소속 프로농구 팀입니다. 데이터는 2008-2009 시즌의 LA 레이커스 경기에 대한 기록입니다.

* Data : http://www.basketballgeek.com/data/

## Purpose & contents

해당 Report는 LAkers의 경기에 대한 분석입니다. 분석 내용은 아래와 같습니다.

- LA레이커스의 홈 경기 vs. 원정경기 비율
- 경기에서 선수들이 가장 많이 하는 행동유형(etype)
- 2008-2009 시즌에서 LA레이커스의 경기 결과
- LA레이커스 선수 코트 위치별 동작 유형

## Data 
**columns**
* Date: 경기 일자
* Opponent: 대전 팀
* Game type: 홈경기 vs. 원정경기
* Time: 분 : 초
* Period: 쿼터(한 쿼터당 12분 씩, 동점일 경우 5 쿼터 진행)
* Etype: 유형(ejection / foul / free throw / jump ball / rebound / shot / sub / timeout / turnover / violation 퇴장 / 파울 / 자유투/ 점프볼/ 리바운드/ 슛/ 패스 / 타임아웃/ 턴오버/ 반칙)
* Team: 팀 구분(LAL: LA Lakers, 상대팀)
* Player: 선수명
* Result: 결과
* Points: 점수
* Type: 세부행동
* X, Y: 상대편 팀 골대 뒤에서 바라본 X, Y 좌표. 골대의 위치는 (25, 5.25)이다.

**Data Summary**
* 총 데이터 개수: 450112 
* 총 결측치 수: 76625 = 전체 데이터의 17.02% 
* LA레이커스와 경기한 팀 수: 28 
* 경기에 등장하는 행동 수: 10 
* 경기에 등장하는 세부행동 수: 73

## Conclusion

* LA레이커스의 홈 경기 vs. 원정경기 비율
  <figure>
    <img src="/assets/img/in_post/LAkers/Lg1.png" title="HomeAway">    
    <figcaption>Home-Away 비율</figcaption>
  </figure>
  : 홈 경기와 원정경기를 1:1 비율로 치렀다.
* 경기에서 선수들이 가장 많이 하는 행동유형(etype)
  <figure>
    <img src="/assets/img/in_post/LAkers/Lg2.png" title="type">    
    <figcaption>행동유형</figcaption>
  </figure>
  <figure>
    <img src="/assets/img/in_post/LAkers/Lg3.png" title="quatype">    
    <figcaption>쿼터별 행동유형</figcaption>
  </figure>

   : 슛을 가장 많이 했으며 그 다음으로는 리바운드였다.
* 2008-2009 시즌에서 LA레이커스의 경기 결과
  <figure>
    <img src="/assets/img/in_post/LAkers/Lg4.png" title="matchResult">    
    <figcaption>시즌 경기 결과</figcaption>
  </figure>
  : LA 레이커스는 총 78회의 경기 중, 63번 우승했다.

* LA레이커스 선수 코트 위치별 동작 유형
  <figure>
    <img src="/assets/img/in_post/LAkers/Lg6.png" title="matchResult">    
    <figcaption>위치별 동작 유형</figcaption>
  </figure>
 
  <figure>
    <img src="/assets/img/in_post/LAkers/Lg5.png" title="matchResult">    
    <figcaption>Position of successful shot</figcaption>
  </figure>
  
  : 상대편 골대 기준으로 왼쪽에서 슛 했을 때 더 많이 성공했다

  ## Code
  
  {% include_relative IPY/LAkers.html %}