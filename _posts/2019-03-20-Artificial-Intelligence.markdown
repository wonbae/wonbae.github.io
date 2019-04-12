# 인공지능 (Artificial Intelligence) 개론


>What can AI do for you?
인공지능이 우리에게 무엇을 해줄 수 있을까?


- Autonomous Driving(자율주행, 테슬라,구글,네이버)
- Handwriting Recognition(손글씨 인식)
- Sentiment Analysis(글의 긍정부정을 알아내는)
- Machine Translations(번역)

Humans vs. Machines
- 1997 : Deep Blue(chess)
 - tree 탐색 알고리즘
- 2011 : IBM Watson(Jeopardy)
- 2016 : AlphaGo
 - 기계학습 알고리즘(딥러닝, reinforce learning : 강화학습)


 - Virtual Assistants
  - Amazon Echo의 음성 인식률이 높음

  - Dialog System
  	- Chat bot 
  	- Tutor robot
  	- 자율주행 시 자동차와 대화


 - Computational Complexity
 - Information Complexity
 > 인공지능으로 최적의 솔루션을 찾기가 너무나 많은 시간이 걸리므로 그것 보단 근접 솔루션을 찾는다. 이걸 위해 많은 데이터를 필요로 한다.

 - Resources
 	- Computation(time/memory)
 	- Information(data)

 AlphaGo, NVIDIA Auto Driving, Google Translation 등의 예를 통해 알 수 있는 AI 방식은
 > BigData + Hardware + Machine Learning Algorithm 이다 
 
 ---
 ---
 # What is CT(Computational Thinking)
 
 > CT는 문제에 대 접근방법과 문제해결 능력입니다.
 
 여기서 문제해결 능력이란, 많은 사람들이 평소 일상생활에서 경험한 것들입니다.
 수학, 과학, 인문학 등의 분야에서 문제를 찾아내고 해결해 내는 방법들에 대한 과정 혹은 능력을
 이론화 한것입니다. CT는 각 분야(Domain)에 강력한 요소로 작용합니다.
 
 - **특징 및 요소(Feature)**
 > 분해(Decomposition) : 자료, 과정, 문제를 작고 다룰 수 있는 부분으로 나누기
 > 패턴 인식(Pattern Recognition) : 데이터안에 있는 패턴, 동향, 규칙들을 관찰하기
 > 추상화(Abstraction) : 이 같은 패턴들을 만드는 일반 원칙 정하기
 > 알고리즘 설계(Algorithm design) : 이 문제나 유사한 문제를 풀기 위한 단계적 방법 만들기
 > 자동화(Automatically) : 프로그램을 통한 자동화와 디버
 
 이를 통한 각 데이터에 대한 문제에서 Insight를 찾아냅니다.
 
 
# What is Differnet AI, ML, DL

 > 모두 BigData를 기반으로 활용된다는 점에서 공통점이 있지만,
   넓은 범위의 AI에서 ML은 AI를 구현하는 하나의 방법이고 DL또한 ML 중 하나의 방법이다
   AI > ML > DL
   
- **AI(Artificial Intelligence)**
  - 인간과 비슷한 컴퓨터를 만든다는 목표로 인간의 신경망등을 모방하여 그에 준하는 인간의 사고력등을 연구 및 개발
  
- **ML(Meachine Learning)**
    인공지능을 구현하는 구체적인 방법 및 접근방식 
    
  `1. 지도학습(Supervised Learing)`
    - 결과를 맞다 아니다 정답 알려주며 가르킴
    - 빅데이터를 정리, 분석하여 학습하고 이를 바탕으로 판단이나 예측을 하는 것. 보통 testset와 trainset을 나눠서 학습
    - `Regression(회귀분석)`
      - `선형 그래프` 형태로 정의될 수 있는 문제들에 대해, 변화되는 값을 따라 추적하여 기존의 데이터를 학습하고 그를 바탕으로 새로운 데이터를 통해 예측 모델링하는 방법
    - `Classification(분류)`
      - 데이터의 Category관계를 파악하여 0,1 형식처럼 조건에 맞는지 판별하는 알고리즘, 새로운 데이터의 카테고리도 판별한다
      - ex) Decision Tree Algorithm, 스팸메일, 점수 등급, 문자 판별

  `2. 비지도학습(UnSupervised Learing)`
    - 정답 안알려주는것
    - 레이블, 카테고리가 없는 데이터에서 어떤 관계를 스스로 찾아내는 방법으로 사람의 개입이 없어서 비지도 학습
    - ex) Clustering (비슷한 데이터들의 집합, 데이터의 특성을 고려해 그룹을 정의하고, 다른 클러스터 개체보다 더 유사한 개체로 그룹핑)
    - 클러스터링을 통해 비슷한 놈들끼리 특징을 파악할 수 있음, 데이터 전처리할때 사용되기도 함
    
  `3. 강화학습(Reinforcement Learnig)`
      - 기초 데이터를 주지 않아도 스스로 학습을 통해 결과를 도출하는 방법을 알아가는 방법.
      - 제어나 게임 플레이 등 상호작용을 통해서 최적의 동작을 학습, 액션에 대한 보상을 얻는 과정 반복
      - ex) 딥마인드의 벽돌깨기 게임
  
  
- **DL(Deep Learning)**
  - 완전한 머신러닝을 구현하는 기술
  - 인공신경망에서 발전한 형태의 인공지능으로, 뇌의 뉴런과 유사한 정보 입출력 레이어를며 상을 최대화하고 벌을 최소화 하도록 강화 학습하는 방식.

알파고가 이 방법으로 학습 되었고, 주로 게임에서 최적의 동작을 찾는데 쓰는 학습 방식이다.

며 상을 최대화하고 벌을 최소화 하도록 강화 학습하는 방식.

알파고가 이 방법으로 학습 되었고, 주로 게임에서 최적의 동작을 찾는데 쓰는 학습 방식이다.


우리들도 인생에서 강화학습을 하며 살아왔다.
우리들도 인생에서 강화학습을 하며 살아왔다. 활용해 데이터를 학습,

 
 # Python 특징
 1. `플랫폼 독립적` : OS상관 없이 사용됨
 2. `인터프리터 언어` : 컴파일 언어(소스코드를 기계어로 번역)와 다르게 소스코드 한줄 읽고 바로 실행해주는 특지(Just In Time)
 3. `OOP언어` : 문제해결을 객체라는 관점으로 분석하여 데이터와 메서드를 사용하여 프로그램을 작성하는 방식
 4. `동적타이핑 언어`: 변수의 타입을 먼저 정의하는 것이 아닌, 프로그램실행 시 각 데이터변수의 타입을 결
 
 
 
# OOP(Object Oriented Programming)
> 추상화, 캡슐화, 상속, 다형성
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 


