---
title: "[NLP] Transformer"
tags:
    - Transformer
    - DAY19 TIL
use_math: true
---

Boostcamp Day 19. 2021-02-18.


# Natural Language Processing (NLP) - Transformer

### Contents
-
- Multi-Head Attention

## Intro
이번 강의에서는 현재 NLP 연구 분야에서 가장 많이 활용되고 있는 Transformer(Self-Attention)에 대해 자세히 알아봅니다. Self-Attention은 RNN 기반 번역 모델의 단점을 해결하기 위해 처음 등장했습니다. RNN과 Attention을 함께 사용했던 기존과는 달리 Attention 연산만을 이용해 입력 문장/단어의 representation을 학습을 하며 좀 더 parallel한 연산이 가능한 동시에 학습 속도가 빠르다는 장점을 보였습니다


# Transformer : Multi-Head Attention
- Maximum path lengths, per-layer complexity and minimum number of sequential operations for differnt layer types.
    - $n$ is the sequence length
    - $d$ is the dimension of representation.
    - $k$ is the kernel size of convolutions
    - $r$ is the size of the neighborhood in restricted self-attention.

# Transformer : Block-Based Model
- Each block has two sub-layers
    - Multi-head attention
    - Two-layer feed-forward NN(with ReLU)
- Each of these two steps also has
    - Residual connection and layer normalization
    - $LayerNorm(x+sublayer(x))$

# Transformer : Layer Normalization
- Layer nomalization changes input to have zero mean and unit variance, per layer and per training point(and add two more parameters)
- Layer normalization consists of two steps:
    - Normalization of each word vectors to have mean of zero and variance of one.
    - Affine transformation of each sequence vector with learnable parameters.

# Transformer : Positional Encoding
- RNN은 순서에 대해서 적용할순 있지만 Transformer의 self-attention은 `순서`가 바뀌는거에 대해서 캐치를 못하기 때문에 Positional Encoding이 사용된다.
- Use sinusoidal functions of different frequencies.
    - 특정한 벡터를(sin,cos) 순서를 파악하고자 하는 특정 벡터에 더해줌으로써 서로다른 순서를 파악할 수 있도록 한다.
    - 주기함수를 사용.
    - $PE_{pos,2i} = sin(pos/{10000^{2i/d}model})$
    - $PE_{pos,2i} = cos(pos/{10000^{2i/d}model}) $

# Transformer : Warm-up Learning Rate Scheduler
- learning rate hyper-parameter를 학습과정 중간에 적절히 변경하는 것을 말함. 처음에 딱 정해놓고 쭉 하기보단 중간중간 바꿔보겠다는거.

# Transformer : Decoder
- Two sub-layer changes in decoder
- Masked decoder self-attention on previously generated output
- Encoder-Decoder attention, where queries come from previous decoder layer and keys and values come from output of encoder.


# Transformer : Masked Self-Attention
- Those words not yet generated cannot be accessed during the inference time.
- Renormalization of softmax output prevents the model from accessing ungenerated words.


<br><br><br><br>

## Further Reading
- [Attention is all you need, NeurIPS'17](https://arxiv.org/abs/1706.03762)
- [Illustrated Transformer](http://jalammar.github.io/illustrated-transformer/)
- [Annotated Transformer](http://nlp.seas.harvard.edu/2018/04/03/attention.html)
- [Group Normalization](https://openaccess.thecvf.com/content_ECCV_2018/papers/Yuxin_Wu_Group_Normalization_ECCV_2018_paper.pdf)

## Further Question
- Attention은 이름 그대로 어떤 단어의 정보를 얼마나 가져올 지 알려주는 직관적인 방법처럼 보입니다. Attention을 모델의 Output을 설명하는 데에 활용할 수 있을까요?  
참고: [Attention is not explanation](https://arxiv.org/pdf/1902.10186.pdf)  
참고: [Attention is not not explanation](https://www.aclweb.org/anthology/D19-1002.pdf)


## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.

