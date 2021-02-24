---
title: "[Graph 6] Graph를 추천시스템에 어떻게 활용할까? (기본)"
tags:
    - Graph
    - 내용 기반 추천
    - 협업 필터링
    - DAY23 TIL
use_math: true
---

Boostcamp Day 23. 2021-02-24.

# Graph in AI - Recommendation System

### Contents
- 내용기반 추천(Contents based Recommendation)
- 협업 필터링(Collaborative Filtering)
- 추천 시스템의 평가

## Intro
넷플릭스와 유투브의 컨텐츠 추천, 아마존의 상품 추천 등 우리는 일상생활 속 다양한 곳에서 추천 시스템을 사용하고 있습니다. 이번 강의에서는 다양한 형태의 추천시스템 중 아이템의 내용을 사용해 추천해주는 `'내용 기반 추천(contents based recommendation')`과, 유저와 아이템간의 유사도를 통해 추천을 해주는 `'협업 필터링(collaborative filtering)'`에 대해 공부해봅니다. `각 알고리즘의 장단점에 집중`하면서 강의를 들어봅시다!

<br>

추천 시스템은 사용자 각각이 구매할 만한 혹은 선호할 만한 상품/영화/영상을 추천합니다.
> Graph 관점에서 추천 시스템은 `미래의 간선을 예측하는 문제` 혹은 `누락된 간선의 가중치를 추정하는 문제`로 해석할 수 있음.

<br>

# 내용 기반 추천시스템(Contents based Recommendation)
> 내용기반 추천은 각 사용자가 구매/만족햇던 상품과 유사한 것을 추천하는 방법.  

ex)
- 동일한 장르의 영화를 추천하는 것  
- 동일한 감동의 영화 혹은 배우가 출현한 영화를 추천.
- 동일한 카테고리의 상품을 추천하는 것.

## 원리
- 첫 단계로 사용자가 선호했던 상품들의 `상품 프로필(Item Profile)`을 수집하는 단계.
    - 상품 프로필이란, 해당 상품의 특성을 나열한 `벡터`임
- 다음 단계는 `사용자 프로필(User Profile)`을 구성하는 단계입니다.
    - 사용자 프로필은 선호한 상품의 상품 프로필을 선호도를 사용하여 가중 평균하여 계산한다. 즉 사용자 프로필 역시 벡터임.
- 다음 단계는 사용자 프로필과 다른 상품들의 상품 프로필을 매칭하는 단계.
    - 사용자 프로필 벡터 $\vec u$와 상품 프로필 벡터 $\vec v$
    - `코사인 유사도` $\vec u \cdot \vec v \over {\lVert \vec u \rVert \lVert \vec v \rVert}$ 를 계산합니다. 즉, 두 벡터의 사이각의 코사인 값을 계산합니다.
    - 각이 좁을 수록 유사도가 높은거고 각이 크면 유사도가 낮은거임.

## 장단점


<br>


# 협업 필터링(Collaborative Filtering)

<br><br>

## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.

