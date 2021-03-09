---
title: "[CV3] Image Classification 2"
subtitle: 
tags: [computer vision, image classification, ResNet, GoogLeNet, CNN] 

---

Boostcamp Day 32. 2021-03-09.
DAY32 TIL

# Computer Vision - Image Classification 2

### Contents
1. Problems with deeper layers
    - Going deeper with convolutions
    - Hard to optimize
2. CNN architectures for image classification 2
    - GoogLeNet
    - ResNet
    - Beyond ResNet
3. Summary of image classification
    - Summary of image classification
    - CNN backbones

<br>

## Intro
이번 강의에서는 1강 Image Classification에 이어서 대표적인 CNN 모델들에  대해 배웁니다.
먼저 VGGNet과 비슷한 시기에 등장한 GoogLeNet을 시작으로, 지금도 많이 쓰이고 있는 ResNet에 공부하고 실습을 진행합니다.
이 외에도 추가적으로 몇가지 CNN 모델들에 대한 소개를 합니다.
끝으로 1강과 3강까지 다룬 4가지 모델 (AlexNet, VGGNet, GoogLeNet, ResNet)에 대하여 메모리 측면과 계산 효율 관점에서 비교 분석을 합니다.

<br>

# 1. Problems with deeper layers
## Going deeper with convolutions
- The neural networks is getting deeper and wider
    - 뉴럴넷이 더 깊어지고 더 넓어지고 있다.
- Deeper networks learn more powerful features, because of  
    - Larger receptive fields
    - More capacity and non-linearity  

    즉, 더 많은 것들을 수용할 수 있을만큼 규모가 크고, 더 많은 용량과 non-linearity(?) 때문에 network를 deep하게 쌓는게 아주 효과적이다.
- But, getting deeper and deeper always works better?  
    근데 더욱 더 깊어지면 더 좋을까?

## Hard to optimize
아니다. 깊어진다고 다 좋은게 아니다.
- Deeper networks are harder to optimize.  
    깊어 질수록 최적화 하는게 학습하는게 어렵다. 이유는

    - Gradient vanishing / exploding
    - Computationally complex
    - ~~Overfitting problem~~ Degradation problem

    깊어 질수록 Gradient가 희미해지거나 너무 커지는경우,  
    계산 복잡도가 너무 빡센경우  
    과적합이 생기는줄 알았지만 알고보니 학습이 덜 되는 경우 등이 문제점이다.

<br>

# 2. CNN architectures for image classification 2
## GoogLeNet
Deeper network with computational efficiency.

- Inception module
    - 









<br><br>

## Further Reading
- [ResNet](https://arxiv.org/pdf/1512.03385.pdf)

## Reference

- bootcamp AI Tech pdf.  
- NAVER Connect Foundation.

