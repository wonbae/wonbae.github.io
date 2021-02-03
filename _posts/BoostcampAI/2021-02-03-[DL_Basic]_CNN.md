---
title: "[DL_Basic] CNN(Convolutional Neural Networks)"
tags:
  - CNN
  - DAY13 TIL
use_math: true
---

Boostcamp Day 13. 2021-02-03.


# Deep Learning Basics

### Contents
- CNN (Convolutional Neural Networks)
- Modern CNN Network list
    - AlexNet
        - 최초로 Deep Learning을 이용하여 ILSVRC에서 수상.
    - VGGNet
        - 3x3 Convolution을 이용하여 Receptive field는 유지하면서 더 깊은 네트워크를 구성.
        [Receptive field 참고 자료](https://cs231n.github.io/convolutional-networks/#conv)  
    - GoogLeNet
        - Inception blocks 을 제안.
    - ResNet
        - Residual connection(Skip connection)이라는 구조를 제안.
        - h(x) = f(x) + x 의 구조
    - DenseNet
        - Resnet과 비슷한 아이디어지만 Addition이 아닌 Concatenation을 적용한 CNN.



## Intro
1. CNN(Convolutional Neural Network)에서 가장 중요한 연산은 Convolution 입니다.
CNN에 대한 공부를 하기 전에 Convolution의 정의, convolution 연산 방법과 기능에 대해 배웁니다.
그리고 Convolution, 입력을 축소하는 Pooling layer, 모든 노드를 연결하여 최종적인 결과를 만드는 Fully connected layer 로 구성되는 기본적인 CNN(Convolutional Neural Network) 구조에 대해 배웁니다.  

2. ILSVRC라는 Visual Recognition Challenge와 대회에서 수상을 했던 5개 Network 들의 주요 아이디어와 구조에 대해 배웁니다.

3. Computer Vision 에서 CNN을 이용한 분야를 알아보고자 합니다.
Semantic segmentation의 정의, 핵심 아이디어에 대해 배웁니다. 
Object detection의 정의, 핵심 아이디어, 추가적으로 종류에 대해 배웁니다. 



# CNN (Convolutional Neural Networks)









<br><br><br><br>

## Reference

- bootcamp AI Tech pdf  


