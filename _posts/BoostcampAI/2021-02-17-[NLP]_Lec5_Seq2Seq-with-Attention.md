---
title: "[NLP] Sequence to Sequence with Attention"
tags: [NLP, seq2seq, Attention, Encoder, Decoder]
use_math: true
---

Boostcamp Day 18. 2021-02-17.
DAY18 TIL

# Seq2Seq with Attention


### Contents
- Seq2Seq with attention
- Encoder-decoder architecture
- Attention mechanism

## Intro
Sequence를 Encoding와 Decoding할 수 있는 sequence to sequence에 대해 알아봅니다.

Sequence to sequence는 encoder와 decoder로 이루어져 있는 framework으로 대표적인 자연어 처리 architecture 중 하나입니다. Encoder와 Decoder로는 다양한 알고리즘이 사용될 수 있지만 이번 시간에는 `RNN과 Attention을 결합한 sequence to sequence` 모델을 학습합니다.

앞선 강의에서 설명드렸던 것처럼 RNN 모델이 갖고 있는 단점을 보완하고자 Attention(논문에서는 alignment로 표현되고 있습니다) 기법이 처음 등장했습니다. 다양한 Attention의 종류와 이를 활용한 translation task에 대해서 알아봅니다

## wiki docs를 살펴보면    
시퀀스-투-시퀀스(Sequence-to-Sequence)는 입력된 시퀀스로부터 다른 도메인의 시퀀스를 출력하는 다양한 분야에서 사용되는 모델입니다. 예를 들어 `챗봇(Chatbot)`과 `기계 번역(Machine Translation)`이 그러한 대표적인 예인데, 입력 시퀀스와 출력 시퀀스를 각각 질문과 대답으로 구성하면 챗봇으로 만들 수 있고, 입력 시퀀스와 출력 시퀀스를 각각 입력 문장과 번역 문장으로 만들면 번역기로 만들 수 있습니다. 그 외에도 *내용 요약(Text Summarization), STT(Speech to Text)* 등에서 쓰일 수 있습니다.  

하지만  

시퀀스투시퀀스 모델은 인코더에서 입력 시퀀스를 컨텍스트 벡터라는 하나의 고정된 크기의 벡터 표현으로 압축하고, 디코더는 이 컨텍스트 벡터를 통해서 출력 시퀀스를 만들어냈습니다.  

RNN 기반의 Seq2Seq 모델은 두가지 문제가 있다.  

- 첫째, 하나의 `고정된 크기`의 벡터에 모든 정보를 `압축`하려고 하니까 `정보 손실`이 발생합니다.  
- 둘째, RNN의 고질적인 문제인 `기울기 소실(Vanishing Gradient)` 문제가 존재합니다.  

> 즉, 결국 이는 기계 번역 분야에서 입력 문장이 길면 번역 품질이 떨어지는 현상으로 나타났습니다. 이를 위한 대안으로 입력 시퀀스가 길어지면 출력 시퀀스의 정확도가 떨어지는 것을 보정해주기 위한 등장한 기법인 `어텐션(attention)`을 사용한다.

<br>

## Recall(복습): Types of RNNs
- Sequence-to-sequence
    - Machine Translation

여러가지 형태의 RNN Task가 있는데 Seq2Seq 같은 경우에는 many to many에 해당하고 seq를 여러개 받아들여 여러개의 seq를 출력한다.
그리고 위에서 말했듯이 주로 기계번역에 사용된다.

<br>

# Seq2Seq with Attention
- 


- it takes a sequence of words as input and gives a sequence of words as output.
- it composed of an encoder and a decoder.
- encoder와 decoder는 서로 다른 모델이고 서로 다른 하이퍼파라미터를 갖는다. 다만 둘사이의 연결은 어느정도 있어야 하는데 encoder에서의 정보를 잘 저장해서 decoder에 처음 부분에 thought vector로써 h0를 주면 디코더가 동작하는구조.

<br>

# Encoder-decoder architecture
- encoder를 각각 거칠때마다 2개의 output이 나오는데 하나는 다음 encoder로 향하고 하나는 attention score를 구하기위해 나중에 디코더의 hiddent state vector와 함께 계산되어 Attention distribution을 만든다. 이렇게 마지막에 나오는 state vector는 aattention의 output이고 이것을 어떻게 사용하냐면, decoder의 벡터와 concat을 해서 다음번 나올 단어를 예측한다.

- Teacher forcing  
    학습 초반에는 Decoder의 input으로 Ground Truth(정답)을 일부러 넣어줘서 방향을 잡아준 다음에 학습을 진행하는 경우를 teacher forcing이라함.  
    그런다음 학습이 잘 된다 싶으면 decoder가 예측한 값을 다음번 decoder input으로 사용한다.

<br>

# Attention Mechanism
encoder의 hidden state vector와 decoder의 hidden state vector사이의 유사도를 구하는 방식은 내적을 통해서 계산을 했었는데.   
유사도를 구하는 다른 방법에 대해서도 살펴보자.

3가지 방법
- dot
- general
- concat

$수식$

<br>

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


<br><br>

## Further Reading

- [Sequence to sequence learning with neural networks, ICML’14](https://arxiv.org/abs/1409.3215)
- Effective Approaches to Attention-based Neural Machine Translation, EMNLP 2015  
- CS224n(2019)_Lecture8_NMT


## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.
- [wiki docs](https://wikidocs.net/24996)
