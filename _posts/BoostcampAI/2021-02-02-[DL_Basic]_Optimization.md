---
title: "[DL] Optimization 최적화 방법"
tags:
  - Optimization
  - DAY12 TIL
use_math: true
---

Boostcamp Day 12. 2021-02-02.

# Deep Learning Basics

### Contents
- Important Concepts in Optimization
    - Generalization
    - Under-fitting vs. over-fitting
    - Cross validation
        - Time Series Nested Cross-Validation
    - Bias-variance tradeoff
    - Bootstrapping
    - Bagging and boosting
- Gradient Descent Methods
    - Stochastic gradient descent
    - Momentum
    - Nesterov accelerated gradient
    - Adagrad
    - Adadelta
    - RMSprop
    - Adam
- Regularization
    - Early stopping
    - Parameter norm penalty
    - Data augmentation
    - Noise robustness
    - Label smoothing
    - Dropout
    - Batch normalization

## Intro
이번 시간은 다양한 최적화 방법에 대해서 다뤄보겠다. 학습을 진행함에 있어서 보다 잘 학습되고 빠르게 학습하기 위해서는 다양한 기법들이 사용된다. 각각의 특징과 장단점을 알고가는 시간이 되길바란다. 그리고 최적화는 절대적인 방법이 아니라 데이터에 따라, 모델에 따라 선택방법이 달라진다. 그렇기 때문에 대채적으로 무슨 기법이 있는지 알고 있어야 때에 따른 적용방법도 알수있지 않을까용?

<br>

# Important Concepts in Optimization
최적화에 있어서 알고 있어야할 중요한 특징이 있다. 
1. 왜 최적화가 필요하며
2. 어떤 상황에서 최적화를 해야하는가?
3. 최적화를 하면 어떠한 방법으로 할껀가?  

연장(6각나사, 몽키스패너 등)이 있다면 어떻한 상황에서 어떻게 쓰는건지 알고 써야할 것이다. AI를 활용해 문제해결을 하는 우리의 목적은 모델을 잘 학습시켜서 실제 상황에서 잘 동작하는 것이다. 학습을 진행할때 잘 되다가 실전상황에서 잘못동작하거나 잘못된 예측을 하면 안될것이다. 

<br>

## Generalization


