---
title: "[Graph5] Graph의 구조를 어떻게 분석할까?"
tags:
    - Graph
    - Community
    - DAY23 TIL
use_math: true
---

Boostcamp Day 23. 2021-02-24.


# Graph in AI - Community

### Contents
- 군집 탐색의 정의
- 군집 탐색 알고리즘
- 중첩이 있는 군집 탐색

## Intro
이번 강의에서는 그래프에서의 군집(Community)이 무엇인지 배우고, 군집에 대한 해석, 그래프에서 군집을 탐색하는 법에 대해 배웁니다.

실제 세상에서 우리는 주변에서 여러가지 종류의 군집을 볼 수 있습니다. 인간 관계 사이에서 (ex. 동아리, 동창회), 화학 물질 내부에서 등 `어디서나` 군집을 발견할 수 있습니다. 그렇다면, 우리는 그래프 데이터에서 `군집을 어떻게 정의`하고, `어떻게 찾아`낼까요? 

이번 장을 통해서 그래프 데이터에서 군집을 찾아내는 알고리즘을 배워보고, 실제로 적용까지 해보겠습니다!




# 군집성의 정의
> 군집 탐색의 성공 여부를 판단하기 위해서, `군집성(Modularity)`가 사용됨.

그래프와 군집들의 집합 S가 주어졌다고 하면
각 군집 $s \in S$ 가 군집의 성질을 잘 만족하는지를 살펴보기 위해,
군집 내부의 간선 수를 `그래프와 배치 모형`에서 비교함.


${1 \over 2\left\vert E \right\vert} \sum_{s \in S} (그래프에서 군집 s 내부 간선의 수 - 배치 모형에서 군집 s 내부 간선의 수의 기댓값)$

즉, 배치모형과 비교했을 때,  
그래프에서 군집 내부 간선의 수가 월등이 많을 수록 성공한 군집 탐색임.

- 즉, `군집성`은 무작위로 연결된 배치 모형과의 비교를 통해 통계적 유의성을 판단함.
- 군집성은 항상 `-1`과 `+1` 사이의 값을 갖는다.
- 보통 군집성이 `0.3~0.7`정도의 값을 가질 때, 그래프에 존재하는 통계적으로 유의미한 군집들을 찾아냈다고 말할 수 있음.

<br>

# 군집 탐색 알고리즘
- Girvan-Newman Algorithm
- Louvain Algorithm

## Girvan-Newman Algorithm
> 대표적인 `하향식(Top-Down) 군집 탐색 알고리즘`.

전체 그래프에서 탐색을 시작하고  군집들이 서로 분리되로록, `간선을 순차적으로 제거`함.

근데 `어떤 간선`을 제거해야 군집들이 분리될까?

- 바로 서로 다른 군집을 연결하는 `다리(Bridge) 역할의 간선`임.

근데 서로 다른 군집을 연결하는 다리 역할의 간선을 어떻게 찾음?

- 간선의 `매개 중심성(Betweeness Centrality)`을 사용함.  
이는 해당 간선이 `정점 간의 최단 경로에 놓이는 횟수`를 의미함.

## Girvan-Newman Algorithm Summary
1. 전체 그래프에서 시작하고
2. `매개 중심성`이 높은 순서로 간선을 제거하면서, `군집성`을 변화를 기록.
3. `군집성`이 가장 커지는 상황을 복원
4. 이 때, 서로 연결된 정점들, 즉 연결 요소를 하나의 군집으로 간주함.  

즉, 전체 그래프에서 시작해서 점점 작은 단위를 검색하는 `하향식(Top-Down)`방법임.

<br>

## Louvain Algorithm
> `상향식(Bottom-Up) 군집탐색 알고리즘` 입니다.

개별 정점에서 시작해서 점점 큰 군집을 형성함.

이것 또한 `군집성`을 기준으로 군집을 나누는데 동작방식은 다음과 같음.

1. 개별 정점으로 구성된 `크기 1의 군집`들로부터 시작함.  
2. 각 정점 $u$를 기존 혹은 새로운 군집으로 이동함.  
이때, `군집성이 최대화` 되로록 군집을 결정함.
3. 더 이상 군집성이 증가하지 않을 때까지 위의 2) 를 반복함.
4. 각 `군집을 하나의 정점으로하는` 군집 레벨의 그래프를 얻은 뒤 3)을 수행함.
5. 1개의 정점이 나올때까지 4)를 반복.



# 중첩이 있는 군집 탐색


# 5강 정리
1. 군집 구조와 군집 탐색 문제
    - 실제 그래프의 군집들은 무엇을 의미할까?
    - 군집을 어떻게 찾아낼까?
2. 군집 구조의 통계적 유의성과 군집성
    - 배치 모형과의 비교를 통해 군집성을 측정
3. 군집 탐색 알고리즘
    - 하향식 알고리즘: Giravan_Newman알고리즘
    - 상향식 알고리즘: Louvain 알고리즘
4. 중첩이 있는 군집 탐색
    - (완화된) 중첩 군집 모형
5. Girvan-Newman알고리즘 구현 및 적용

<br><br>

## Further Reading
- [stanford-edu](http://infolab.stanford.edu/~ullman/mmds/ch10n.pdf)

## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.
