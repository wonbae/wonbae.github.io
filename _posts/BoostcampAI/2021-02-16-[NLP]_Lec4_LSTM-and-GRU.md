---
title: "[NLP] LSTM and GRU"
tags:
    - LSTM
    - GRU
    - DAY17 TIL
use_math: true
---

Boostcamp Day 17. 2021-02-16.


# Natural Language Processing (NLP) - LSTM and GRU

### Contents
- Long Short-Term Memory(LSTM)
- Gated Recurrent Unit(GRU)

## Intro
RNN을 개선한 알고리즘으로 등장했던 LSTM과 GRU에 대해서 다시 한번 살펴봅니다.  
LSTM과 GRU가 gradient flow를 개선할 수 있는 이유에 대해 조금 더 고민하는 시간이 됐으면 좋겠습니다.

 # Long Short-Term Memory (LSTM)
 - Solving Long-term dependency problem. 즉, 멀리 떨어진 정보들에 대해서도 효과적으로 처리하고 학습할 수 있도록 하는 개선된 방법.
 - 






 # Gated Recurrent Unit (GRU)


# Backpropagation in LSTM/GRU

# Summary on RNN/LSTM/GRU
- RNNs allow a lot of `flexibility` in architecture design.
- Vanilla RNNs are `simple` but don't work very well
- Backward flow of gradient in RNN can `explode or vanish`
- Common to us LSTM or GRU : their additive interactions `improve gradient flow`



<br><br><br><br>

## Further Reading

[Understanding LSTM Networks](http://colah.github.io/posts/2015-08-Understanding-LSTMs/)

## Further Question

- BPTT 이외에 RNN/LSTM/GRU의 구조를 유지하면서 gradient vanishing/exploding 문제를 완화할 수 있는 방법이 있을까요?  
- RNN/LSTM/GRU 기반의 Language Model에서 초반 time step의 정보를 전달하기 어려운 점을 완화할 수 있는 방법이 있을까요?

## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.

