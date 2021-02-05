---
title: "[DL_Basic] Generative Models"
tags:
  - Generative Models
  - DAY15 TIL
use_math: true
---

Boostcamp Day 15. 2021-02-05.

# Deep Learning Basics - Generative Models
### Intro
머신러닝, 딥러닝에서 의미하는 Generative model이 무엇인지, 
이를 이해하기 위한 기본적인 통계 이론, 
다양한 Generative model의 아이디어, 구조에 대해 배웁니다.
지난 강의에서는 Auto-regressive model의 Generative model에 대해 배웠습니다.
Generative models part 2 에서는 실제로 많이 다뤄지는 Practical 한 Generative model인 
Variational Auto Encoder와 Generative Adversarial Network 를 이용하여 Latent variable model 에 대해 배웁니다.


### Contents
Part1
- Structure Through Independece
- Conditional Independece
  - Chain rule
  - Bayes' rule
  - Conditional Independence
- Auto-regressive Model
  - NADE : Neural Autoregressive Density Estimator
  - Pixel RNN

<br>

Part2
- Latent Variable Models
- Variational Auto-encoder
- GAN - Generative Adversarial Network
  - DCGAN
  - Info-GAN
  - Text2Image
  - Puzzle-GAN
  - CycleGAN
  - Star-GAN
  - Progressive-GAN

<br>

# Structure Through Independece
# Conditional Independece
## Chain rule
수식과 함께..
## Bayes' rule
수식과 함께..
## Conditional Independence
수식과 함께..

# Auto-regressive Model
Markov assumption을 포함하는 느낌. 직전 N-1개의 data를 고려할려면 순서를 알아야함.
## NADE - Neural Autoregressive Density Estimator
> 입력의 density를 계산해서
- 무튼 이전 픽셀의 영향을 현재 픽셀이 받기 때문에 서로 의존성이 있다.
- 
## Pixel RNN
> 이미지에 있는 픽셀들을 만들어 내는 모델.

앞에서 본 fully-connected layer 모델들과 달리 RNN을 사용하여 순서대로 생성.
  2가지 구조가 있음 : based on the `ordering` of chain
  순서에 따라 다르다는 말.

  1. Row LSTM : 위쪽의 정보를 이용해서 픽셀을 만듬.
  2. Diagonal BiLSTM : BiLSTM을 활용해서 필셀의 이전정보를 모두 사용. 

# GAN - Generative Adversarial Network

창과 방패 느낌. 서로의 존재로 인해서 서로 발전하는...
generator는 속일려고 노력하고 discriminator는 속지 않을려고 하는거 그래서 서로 발전. 마치 virus와 항체같군요.
주로 위조지폐와 경찰의 예를 들어 설명하는데

- Discriminator objective
  - 
- Generator Objective

## DCGAN
- Deconvolution을 활용함
- Reaky ReLU를 사용
## Info-GAN
- 
## Text2Image
- 문장을 이미지로 생성해 주는거
## Puzzle-GAN
- image안에 subpatch를 만들어서 이미지의 특정부분만 해상도를 높이는거
- 이미지에서 특정부분만 바꿀때(?)
## CycleGAN
- 이미지에서 배경이나 사물을 바꾸는거. domain을 바꾼다고 예기하는데 쉽게말해서 야간 배경의 사진을 낮으로 배경만 바꾼다던지 여름의 풍경을 겨울로 바꾼다던지 얼룩말을 그냥 말과 무늬만 바꾼다던지.
- `Cycle-consistency loss`라는 것을 사용. GAN구조 끼리 바꾸는듯.
## Star-GAN
- 배우들의 얼굴 사진을 감정 keyword에 맞게 변형하는거. domain을 완전히 바꾸는 것이 아니라 조금씩 조정하는 느낌.
## Progressive-GAN
- 고차원의 이미지를 Generation하는거. 자연스럽게 여러 얼굴이 변화하는거.
- latent를 차차 쌓아가면서 1024정도까지 쌓는것.












<br><br><br><br>

## Reference

- bootcamp AI Tech pdf.
- NAVER Connect Foundation.

