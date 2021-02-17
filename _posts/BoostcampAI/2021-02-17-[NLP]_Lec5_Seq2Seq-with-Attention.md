---
title: "[NLP] Sequence to Sequence with Attention"
tags:
    - seq2seq
    - Attention
    - DAY18 TIL
use_math: true
---

Boostcamp Day 18. 2021-02-17.


# Natural Language Processing (NLP) - Seq2Seq with Attention

### Contents
- Seq2Seq with attention
- Encoder-decoder architecture
- Attention mechanism

## Intro
Sequence를 Encoding와 Decoding할 수 있는 sequence to sequence에 대해 알아봅니다.

Sequence to sequence는 encoder와 decoder로 이루어져 있는 framework으로 대표적인 자연어 처리 architecture 중 하나입니다. Encoder와 Decoder로는 다양한 알고리즘이 사용될 수 있지만 이번 시간에는 RNN과 Attention을 결합한 sequence to sequence 모델을 학습합니다.

앞선 강의에서 설명드렸던 것처럼 RNN 모델이 갖고 있는 단점을 보완하고자 Attention(논문에서는 alignment로 표현되고 있습니다) 기법이 처음 등장했습니다. 다양한 Attention의 종류와 이를 활용한 translation task에 대해서 알아봅니다


 ## Recall: Types of RNNs
 - Sequence-to-sequence
    - Machine Translation

many to many에 해당하고 seq를 여러개 받아들여 여러개의 seq를 출력한다.

## Seq2Seq Model
- it takes a sequence of words as input and gives a sequence of words as output.
- it composed of an encoder and a decoder.
- encoder와 decoder는 서로 다른 모델이고 서로 다른 하이퍼파라미터를 갖는다. 다만 둘사이의 연결은 어느정도 있어야 하는데 encoder에서의 정보를 잘 저장해서 decoder에 처음 부분에 thought vector로써 h0를 주면 디코더가 동작하는구조.



## Encoder-decoder architecture
- encoder를 각각 거칠때마다 2개의 output이 나오는데 하나는 다음 encoder로 향하고 하나는 attention score를 구하기위해 나중에 디코더의 hiddent state vector와 함께 계산되어 Attention distribution을 만든다. 이렇게 마지막에 나오는 state vector는 aattention의 output이고 이것을 어떻게 사용하냐면, decoder의 벡터와 concat을 해서 다음번 나올 단어를 예측한다.

- Teacher forcing  
    학습 초반에는 Decoder의 input으로 Ground Truth(정답)을 일부러 넣어줘서 방향을 잡아준 다음에 학습을 진행하는 경우를 teacher forcing이라함.  
    그런다음 학습이 잘 된다 싶으면 decoder가 예측한 값을 다음번 decoder input으로 사용한다.


## Attention Mechanism
encoder의 hidden state vector와 decoder의 hidden state vector사이의 유사도를 구하는 방식은 내적을 통해서 계산을 했었는데.   
유사도를 구하는 다른 방법에 대해서도 살펴보자.

3가지 방법
- dot
- general
- concat

$수식$

## Attention is Great!
- Attention significantly improves NMT performance
    - it is useful to allow the decoder to focus on particular prts of the source
- Attention solves the bottleneck problem
    - Attention allows the decoder to look directly at source; bypass the bottleneck
- Attention helps with vanishing gradient problem
    - Provides a shortcut to far-away states
- Attention provides some interpretability
    - By inspecting attention distribution, we can see what the decoder was focusing on
    - The network just learned alignment by itself


<br><br><br><br>

## Further Reading

- Sequence to sequence learning with neural networks, ICML’14  
- Effective Approaches to Attention-based Neural Machine Translation, EMNLP 2015  
- CS224n(2019)_Lecture8_NMT


## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.

