---
title: "[Graph1] Graph란 무엇이고 왜 중요한가"
subtitle: Graph관련 기초 개념, 인공지능 문제, 중요한 이유
tags: [Graph, Graph AI, GNN, DAY21 TIL]
use_math: true
cover-img: https://images.app.goo.gl/RHZeosLNwHRbSPxs5
thumbnail-img: /assets/bcimg/Graph/graphusage.PNG
share-img: https://images.app.goo.gl/RHZeosLNwHRbSPxs5
---

Boostcamp Day 21. 2021-02-22.


# Graph in AI

### Contents
- 그래프란 무엇이고 왜 중요할까?
- 그래프 관련 인공지능 문제
- 그래프 관련 필수 기초 개념

## Intro
그래프 강의의 첫 시간으로 그래프 이론 및 본 강의에서 다룰 내용에 대해서 짧게 소개하고, 그래프 관련 필수 개념들을 소개하는 시간을 갖습니다.

그래프는 다양한 복잡계(Complex Network)를 분석할 수 있는 언어입니다. 그래프를 통해서 다양한 문제들에 접근하기 전에 정점, 간선, 방향성, 가중치 등 그래프 이론에서 사용하는 개념들에 대해서 배워봅니다. 각 정의들을 명확하게 이해하는 데 집중하면서 강의를 들어주시면 감사하겠습니다. 

최첨단 기술보다는 기초와 직관적인 방법론에 집중합니다. 하지만 그래프 신경망등 최첨단 기술도 일부 소개될 예정.

# 그래프란 무엇일까?
> 그래프(Graph)는 정점 집합과 간선 집합으로 이루어진 수학적 구조입니다.  
 

그래프는 네트워크(Network)로도 불립니다.  
`정점(Vertex)`은 `노드(Node)`로 간선은 `엣지(Edge)` 혹은 `링크(Link)`로도 불립니다.


# Graph란 왜 중요할까?
> 그래프는 복잡계(Complex System)를 효과적으로 표현하고 분석하기 위한 언어이다.

<img src="/assets/bcimg/Graph/graphusage.PNG">

예를들어 뇌(뉴럴간 연결), 지식 그래프, 화학 분자, 단백질 상호작용, 세포간 유사도 그래프, 이미지 분해. SNS, 위키피디아 문서검색 등 적용되고 활용되는 곳이 많다.

- 복잡계는 구성 요소들 간의 상호작용으로 이루어집니다. 상호작용을 표현하기 위한 수단으로 그래프가 널리 사용됩니다.

- 복잡계를 이해하고, 복잡계에 대한 정확한 예측을 하기 위해서는 복잡계 이면에 있는 그래프에 대한 이해가 반드시 필요합니다.

- 그래프를 공부함으로써 복잡계가 등장하는 수많은 분야에 활용될 수 있습니다. 전산학, 물리학, 생물학, 화학, 사회과학 등이 그 예시.

<br>
  
# Graph 관련 인공지능 문제
- 정점 분류(Node Classification) 문제
    - `Twitter`에서의 공유(Retweet)관계를 분석하여, 각 사용자의 정치적 성향을 알 수 있을까?
    - `단백질`의 상호작용을 분석하여 단백질의 역할을 알아낼 수 있을까?
- 연결 예측(Link Prediction)문제
    - 거시적, 미시적으로 바라봄.
    - `페이스북`은 어떻게 진화할까?
- 추천(Recommencdation)문제
    - 각자에게 필요한 물건은 무엇일까?
- 군집 분석(Community Detection) 문제
    - 연결 관계로부터 `사회적 무리(Social Circle)`을 찾아낼 수 있을까?
- 랭킹(Ranking) 및 정보 검색(Information Retrieval)문제
    - `웹(Web)`이라는 거대한 그래프로부터 어떻게 중요한 Web을 찾을까?
- 정보전파(Information Cascading) 빛 바이럴 마케팅(Viral Marketing)문제
    - `정보`는 네트워크를 통해 어떻게 전달될까? 정보전달을 최대화 할 수 있는 방법은?


<br>

# 그래프 관련 필수 기초 개념
- Undirected Graph vs Directed Graph
    - Directed Graph
        - 주체와 대상이 서로 분리될 수 있는경우에 Directed Graph를 사용.
        - 예를들어 Tweeter follower경우.
    - Undirected Graph
        - just 관계
        - 협업 관계 그래프
        - 페이스북 친구 그래프

- 가중치가 없는 그래프(Unweighted Graph) vs 가중치가 있는 그래프(Weighted Graph)
    - Weighted graph
        - 전화 그래프
        - 유사도 그래프
    - Unweighted Graph
        - 페이스북 친구 그래프
        - 웹 그래프
    > 가중치가 의미가 있고 데이터가 추가되었을때 유용하면 바꿀수도 있다. 정답이 없고 상황과 데이터에 따라.

- 동종 그래프(Unpartite Graph) vs 이종 그래프(Bipartite Graph)
    - Unpartite Graph
        - 단일 종류의 정점을 가진다.
            - 웹 그래프
            - 페이스북 친구 그래프
    - Bipartite Graph
        - 두 종류의 정점을 가지고 다른 종류의 정점 사이에만 간선이 연결된다.
            - 전자 상거래 구매내역(사용자, 상품)
            - 영화 출연 그래프(배우, 영화)

- 방향성이 있는 그랩에서 `나가는 이웃`과 `들어오는 이웃`을 구분함.
    - 정점 $v$에서 나가는 이웃(Out-Neighbor)의 집함을 보통 $N_{out}(v)$로 적음.
    - 정점 $v$에서 들어오는 이웃(In-Neighbor)의 집함을 보통 $N_{in}(v)$로 적음.

<br>

# 그래프 표현 및 저장.
## Python Library NetworkX 
graph 생성, 변경, 시각화 할 수 있는 라이브러리. 그래프의 구조와 변화를 분석할 수 있다.  
[NetworkX](https://network.org/documentation/stable/index.html)  
[snap.py](https://snap.stanford.edu/snappy/)



<br><br>

## Reference

- bootcamp AI Tech pdf.
- NAVER Connect Foundation.

### image
- https://images.app.goo.gl/RHZeosLNwHRbSPxs5