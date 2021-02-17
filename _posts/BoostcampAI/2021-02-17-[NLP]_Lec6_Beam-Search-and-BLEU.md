---
title: "[NLP] Beam Search and BLEU"
tags:
    - BLEU
    - Beam Search
    - DAY18 TIL
use_math: true
---

Boostcamp Day 18. 2021-02-17.


# Natural Language Processing (NLP) - Beam Search and BLEU

### Contents


## Intro
문장을 decoding 하는 데에 사용하는 대표적인 알고리즘인 Beam Search와 번역 task에서 번역된 문장을 평가하는 대표적인 metric인 BLEU score를 소개합니다.

언어 모델이 문장을 generation할 때에는 확률값에 기반한 다양한 경우의 수가 존재합니다. 모든 경우의 수를 고려하는 것은 비효율적이며 너무 작은 확률값까지 고려한다면 생성된 문장의 quality가 떨어질 수 있습니다. 가장 높은 확률값을 고려하는 방법 역시 모델이 단순한 generation을 하도록 하게 만드는 단점이 있을 수 있습니다. 이러한 문제의 대안으로 제안된 Beam Search를 알아봅니다.

자연어는 컴퓨터가 이해할 수 있는 방식으로 변환되어 모델의 입력 및 출력으로 활용되기 때문에 적절한 metric을 이용해 모델을 평가해야 합니다. 다양한 자연어처리 관련 metric이 있지만, 그중에서도 번역 task에서 가장 대표적인 BLEU score를 소개합니다. 번역에 있어서 BLEU score가 precision을 고려하는 이유에 대해서 고민하면서 강의를 들어주시면 좋을 것 같습니다.

## Greedy decoding
seq2seq with attention방법이 greedy aproch라고 한다. 왜냐하면 현재 time step에서 그 다음 예측해야하는 가장 좋아보이는 단어만을 바라보고 진행하기 때문이다. 잘못 단어를 예측한걸 알았더라도 못돌아간다.  
이를 어떻게 해결할까?

## Exhaustive search
greedy는 그 순간에 최선인 단어 하나만을 고르는 방법이라고 한다면 이것은 가능한 모든 경우를 다 계산해서 들고 있겠다는 방법.
- We could try computing all possible sequences $y$
    - This means that on each step $t$ of the decoder, we are tracking $V^t$ possible partial translations, where $V$ is the vocabulary size
    - This $O(V^t)$ complexity is far too expensive!

## Beam search
이건 앞전의 두개 사이에 위치한 느낌. 
- Core idea: on each time step of the decoder, we keep track of the $k$ most probable partial translations(which we call hypothesis)
    - 우리가 정한 k개만 정해놓겠다.






<br><br><br><br>

## Further Reading
- [Deep learning.ai-BeamSearch.]()
- [Deep learning.ai-RefiningBeamSearch.]()
- [OpenNMT-beam search.]()

## Further Question

BLEU score가 번역 문장 평가에 있어서 갖는 단점은 무엇이 있을까요?  
[참고: Tangled up in BLEU: Reevaluating the Evaluation of Automatic Machine Translation Evaluation Metrics]()

## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.

