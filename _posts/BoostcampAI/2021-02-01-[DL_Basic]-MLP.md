---
title: "[DL] Neural Networks & MLP(Multi-Layer Perceptron)"
tags:
  - MLP
  - Neural Network
  - MSE
  - CE
  - MLE
  - DAY11 TIL
use_math: true
---

Boostcamp Day 11. 2021-02-01.

# Deep Learning Basics

### Contents

- Neural Networks (NN)
- Multi-Layer Perceptron (MLP)
- MSE (Mean Squre Error)
- CE (Cross Entropy)
- MLE (Maximum Likelihood Estimate)
- Pytorch Loss Function

<br>

## Intro
먼저 뉴럴렛이 무엇인지, 어디서 아이디어를 들고왓으며 어떠한 역할을 하는지 알아보고 뉴럴렛을 가능하게 하는 방법이 무엇인지 알아본다. 이때 MLP를 기반으로 초기의 뉴럴렛을 만든게 아닌가 생각한다. 기존의 퍼셉트론에서 여러개의 퍼셉트론으로 붙여서 사용하는 것이 MLP이다. 그리고 MSE, CE, MLE와 같은 Loss 손실함수에 대해서 각각 알아보고 무엇이 서로 다르고 어떠한 상황에서 사용하는 것인지 알아본다. 그리고 Pytorch에서 어떻게 사용되는지 알아본다. 파라미터는 무엇이 들어가는지 등등. 목적은 Pytorch 코드를 보고 Input값과 Output이 대강 어떻게 된다를 알 수있고 파라미터 옵션에 따른 변화를 읽을줄아는 것을 목표로.

<br><br>

# Neural Networks (NN)
위키피디아의 정의는 
> "Neural Networks are computing systems vaguely inspired by the biological neural networs that constitute animal brains." 

라고 적혀 있다. 즉, 사람이나 동물의 생물학적인 `뉴런의 신호전달 방식에서 영감을 얻어서 만들어진 컴퓨팅 시스템`이라고 한다. 전공지식이 없는 사람에게 설명하기 좋은 일반화된 설명이다. 

우리의 뇌는 뉴런으로 엃혀있고 100% 정확히는 모르지만 서로 상호작용하면서 학습을 하고 기억을 한다고 우리는 알고있다. 그래서 컴퓨터도 이와 비슷하게나마 `차용`한것이지 절대 똑같다고는 할 수 없다. 심지어 우리의 인지와 기억, 학습방법에 대해서도 정확히 모르기 때문이다.

이와 같이 최성준 교수님은 아이디어를 빌려왔다고 해서 똑같아야 하는 법도 없고 그럴 필요도 없다. 그래서 뉴럴렛이 뭐냐고 묻는다면 위의 말보다는 아래와 같은 설명이 더욱 설득력 높다고 말씀하신다. 
> "Neural Networks are function approximators that stack affine transformations followed by nonlinear transformations."  
뉴럴넷은 `함수의 근사치`를 구하는 `행렬과 비선형의 연산이 반복적으로 연산되는 수학적인 작업`이다.



비행기의 변천과정을 보여주면서 성준교수님이 말씀하시길 하늘을 날고싶다고해서 꼭 새처럼 날필요는 없다. 물론 처음엔 새를 보고 하늘을 날고싶다는 생각과 동작을 차용할순있지만 꼭 새처럼, 사람처럼 생각할 필요는 없다는 논지. 무슨말씀이신지 바로 이해가 됐고 동감한다. 하지만 여기에 필자의 생각을 더하자면, F22전투기는 새보다 빠르게 날수는 있지만 새처럼 비행을 변칙적으로 할수는 없다. 최근에 새처럼 날개짓을 하는 비행기 드론이 개발된걸 봤다. 여기서 느낀건 처음엔 새를 흉내 냈지만 인간의 무지로 정확한 모방은 못해서 정확히 구현을 못한거지 비효율적이라서 라이트 형제가 그런 비행기를 만든것은 아닐꺼란 것이다. 그래서 기술의 진보로 용도에 맞게 새처럼 나는 비행기도, 지금의 비행기도 같이 운영할수도 잇을꺼같다는 생각을 해봤다. 분명 장단점이 존재할것이고 그것을 잘 저울질 할 수 있어야 겠다고 생각했다. 

<br><br>

## Linear neural networs

### data
- 우리가 학습을 진행할때 사용될 데이터, 1차원으로 이뤄진 x,y 한 쌍의 데이터
  - Data : $\left \{ (x_i, y_i) \right \} _{i=1}^{N}$

<br>

### Model
- x 값이 있을때 f(x) 함수에 대입하면 y 값을 얻는다. 우리는 f(x) 이걸 잘 만들고 싶은거다.
- 이 `데이터들을 잘 설명할 수 있는 함수를 모델`이라고 함. 물론 우리가 잘 맞추도록 잘 설명할 수 있도록 도와줘야 함. 어떻게? loss 를 줄임으로써.
- 간단한 Linear neural net 이기 때문에 함부가 일차원이지만 나중에 이것이 복잡하게 서로 엃혀있는 관계를 Deep learning이라고 함.
  - Model : $\hat y = wx + b$
- 물론 절때 이렇게 이쁜 선형모델 없을꺼임. non-linear도 섞여있고 차원도 높고 그럴꺼임. 그땐 행렬로..
  <br>

### Loss
- 입력값과 출력값이 같을수도 다를수도 있다. 그러면 우리는 정답에 가깝게 w,b 조정이 필요하다.
- `원래값과 우리가 예측한 값의 차이`를 줄이는 것이 loss를 줄인다고 말한다.
  - Loss : $loss =  {1\over N} \sum_{i=1}^N (y_i - \hat y_i)^2$
- 데이터를 넣고 그에 맞는 결과값을 비교하면서 적절한 모델을 찾아가는 과정에서 이 로스값을 최소화해나가야 함.
- Loss Function을 줄이는 것이 목표인데 이것을 어떻게?
- 하나 알아둬야 할껀. loss를 줄인다고 항상 우리가 원하는게 나오진 않는다는것.

<br>

### Gradient Desent

> $w \leftarrow w - \mu {\partial loss \over \partial w}$  
> $b \leftarrow b - \mu {\partial loss \over \partial b}$

loss를 w에 대해서 편미분해서 learning rate($\mu$)만큼 곱해서 원래 w에다가 빼주면 그것이 바로 업데이트.

- ${\partial loss \over \partial b} = {\partial \over \partial b}{1 \over N} {\sum_{i=1}^N (y_i - \hat y_i)^2}$
- ${\qquad = }{\partial \over \partial b}{1 \over N} {\sum_{i=1}^N (y_i - wx_i - b)^2}$
- ${\qquad = }- {1 \over N} {\sum_{i=1}^N -2(y_i - wx_i - b)}$

<br>

### Backpropagation
마지막에 나온 `loss function에 대해서 모든 파라미터로 하나씩 편미분` 해주는 것을 말함. 이때 나오는 편미분 값으로 각 파라미터를 업데이트하는걸 GD라고 함.

<br>



# Multi-Layer Perceptron (MLP)
### Beyond Linear Neural Networks
- 여러 차원의 Input output은 행렬을 통해서 할 수 있음. 
- 근데 깊게 갔을때는 행렬을 N번 곱하기만 하면 그냥 별 의미가 없음.
- so we need `Non-Linearity`
  - 선형결합을 N번 반복하는 것이 아니라 `선형결합을 한 후에 Activation Fucntion`(sigmoid, ReLu,tanh)을 통해서 Non-linear Transform을 거치고, 그렇게 얻어지는 Feature vector를 다시 선형결합하고......on and on.. 하면 더 많은 `표현력`을 갖게 된다.
  - Activation Functions
    - Rectified Linear Unit(ReLU)
    - Sigmoid
    - Hyperbolic Tangent(tanh)
    
  - $y = W_2^Th = W_2^Tp(W_1^Tx)$
    - p가 AF이고 뭐 요런 형식이 MLP임.
    - 더 많이 쌓을수도 있겠고.

<br><br>

# MSE (Mean Squre Error)
- `Regresstion Task`에 주로 쓰이는 방법.
- $MSE = {1 \over N} \sum_{i=1}^{N} \sum_{d=1}^{D}(y_i^d - \hat y_i^d)^2$
- 찾을려고 하는 target data와 예측한 값의 차를 제곱한 형태.
- 항상 만족하는 target data를 갖을 순 없다.
  - 만약 target data가 너무 크거나 그러면 그 하나의 값 때문에 모델이 망가질수가 있다는걸 염두하셈.

  <br><br>

# CE (Cross Entropy)
- `Classification`에 쓰이는 loss function.
- $CE = {-}{1 \over N} \sum_{i=1}^N \sum_{d=1}^{D} y_i^d log\hat y_i^d$
- 왜 분류문제에 쓰일까?
  - 뉴럴렛의 출력값 중에서 해당하는 class의 값만 높이겠다는 것임.
  - 이미지 분류 같은 문제에서 10차원(10종류) 이라고 하면 그중에 가장 큰 하나만 신경쓰겠다는 거임.
  - 다른값들 대비 높기만 하면 되니깐 수학적으로 표현하는게 어려우니 CE를 사용하면 편한가보다.. 근데 이게 최적일까?? 생각해봐야함.

  <br><br>

# MLE (Maximum Likelihood Estimate)
- `Probabilistic Task`에 주로 쓰임.
- $MLE = {1 \over N} \sum_{i=1}^N \sum_{d=1}^{D} log \mathcal{N}(y_i^d;\hat y_i^d, 1)\qquad(=MSE)$
- 단순히 모아니면 도로 결정하는 것이 아니라, 긴가민가하는 정보를 찾고 싶을때 그러한 것을 보고 싶을때 사용함.
  - 예를들어, 이 자동차 사진이 트럭인지 승용차인지 구별할때 교통수단이긴한데 트럭일 활률이 쫌 더 높은거 같아 라던지. 이 사람은 확실히 30대야 혹은 이 사람은 30대이긴 한데 쫌 젊은거 같아 라는 이러한 애매모호한 정보를 알고 싶을때 사용하는듯.

<br><br><br><br>

# Pytorch Loss Function













### Reference

bootcamp AI Tech pdf