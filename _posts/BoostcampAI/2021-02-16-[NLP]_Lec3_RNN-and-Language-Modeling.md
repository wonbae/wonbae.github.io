---
title: "[NLP] humm..."
tags:

  - DAY17 TIL
use_math: true
---

Boostcamp Day 17. 2021-02-16.


# Natural Language Processing (NLP)

### Contents
- Basic problem settings
- Model architecture and ho it works

## Intro
자연어 처리 분야에서 Recurrent Neural Network(RNN)를 활용하는 다양한 방법과 이를 이용한 Language Model을 학습합니다.

RNN은 단어간 순서를 가진 문장을 표현하기 위해 자주 사용되어 왔습니다. 이러한 RNN 구조를 활용해 다양한 NLP 문제를 정의하고 학습하는 방법을 소개합니다.

Language Model은 이전에 등장한 단어를 condition으로 다음에 등장할 단어를 예측하는 모델입니다. 이전에 등장한 단어는 이전에 학습했던 다양한 neural network 알고리즘을 이용해 표현될 수 있습니다. 이번 시간에는 RNN을 이용한 character-level의 language model에 대해서 알아봅니다.

RNN을 이용한 Language Model에서 생길 수 있는 초반 time step의 정보를 전달하기 어려운 점, gradient vanishing/exploding을 해결하기 위한 방법 등에 대해 다시 한번 복습할 수 있는 시간이 됐으면 합니다.

 # Basic of Recurrent Neural Networks (RNNs)
 - How to calculate the hidden state of RNNs
    - We can process a sequence of vectors by applying a recurrence formula at every time step.  

    - $h_t = f_w (h_{t-1}, x_t)$  

    - $h_{t-1}$ : old hidden-state vector
    - $x_t$: input vector at some time step
    - $h_t$ : new hidden-state vector
    - $f_w$ : RNN function with parameters $W$
    - $y_t$ : output vector at time step $t$

    > Notice : The same function and the same set of parameters are used at every time step

    - The state consists of a single "hidden" vector $h$
    - $h_t = tanh(W_{hh}h_{t-1} + W_{xh} x_t + b)$

# Types of RNNs
- one-to-one
    - standard Neural Networs
- one-to-many
    - Image Captioning
- many-to-one
    - Sentiment Classification
- many-to-many
    - Machine Translation
    - Video classification on frame level


# Character-level Language Model











<br><br><br><br>

## Further Reading

[The Unreasonable Effectiveness of Recurrent Neural Networks](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)  
[CS231n(2017)_Lecture10_RNN](http://cs231n.stanford.edu/slides/2017/cs231n_2017_lecture10.pdf)

## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.

