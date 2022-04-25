---
title: "[NLI] Entailment as Few-Shot Learner"
subtitle: new approach, named as EFL, that can turn small LMs into better few-shot learners.
tags: 
    - NLI 
    - NLP
    - EFL
    - Entailment as Few-Shot Learner
    - Natural Language Inference
    - SOTA
    - Few-Shot learning
    - NLP Paper Review
    - 1st Rank in Papers with Code 
use_math: true
# cover-img: /assets/img/path.jpg
# thumbnail-img: /assets/img/thumb.png
# share-img: /assets/img/hello_world.jpeg
---

2022-04-26. 첫번째 논문 리뷰.

> Top 1 papers in the SNLI dataset section of papers with code.
    >> Papers with Code(NLI:SNLI dataset 기준)상위 논문.  
    >> 1. Entailment as Few-Shot Learner.
    >> 2. Self-Explaining Structures Improve NLP Models.
    >> 3. CONDITIONALLY ADAPTIVE MULTI-TASK LEARNING: IMPROVING TRANSFER LEARNING IN NLP USING FEWER PARAMETERS & LESS DATA.
    >> 4. Semantics-aware BERT for Language Understanding.

- Contents
    - Abstract
    - Introduction
    - Related Work
    - Framework of Entailment Training
    - Experiment
    - Optimizations
    - Conclusion
    - A Experiment Details

# Abstract
Large pre-trained language models (LMs) 은 few-shot learners로써 놀라운 능력을 보여줬다. 하지만 LMs는 Train하거나 Serving하는게 힘들만큼 존나 큰 파라미터 스케일링(증감)에 따라 성공여부가 달라진다.

그래서 우리가 이 논문에서 제인하는 것은, 작은 LMs를 더 나은 Few-Shot Learner로 바꾸는 `EFL`이라는 새로운 접근 방식이다.

> reformulate potential `NLP task` into an `entailment` one, and then `fine-tune` the model with as little as 8 examples.

이 접근 방식의 key idea는 *잠재적인 NLP task를 `Entailment`(의미론적 or 수반작업)로 재정의(reformulate)해서 8개의 예제로 모델을 `Fine-tune`(미세조정)* 하겠다.

- 블로그 작성자 피셜 : 뒤에 자세히 나오겠지만, 기존의 NLI 를 해결하는 접근 방식에서 쫌 색다르게 데이터셋을 살짝 변형한다는거 같다. 기존의 문장의미를 포괄하는 새로운 문장을 추가한다는 의미에서 entailment(상속인 지정, 수반)라는 단어가 쓰여진거 같다.

우리는 제안된 방법이,  
(i) `unsupervised contrastive`(대조) `learning-based data augmentation` 방법과 자연스럽게 결합될 수 있음을 추가로 보여줍니다.

(ii) `multilingual`(다국어) few-shot learning으로 `쉽게 확장`됩니다. 18개의 표준 NLP 작업에 대한 체계적인 평가는 이 접근 방식이 다양한 기존 SOTA 퓨샷 학습 방법을 `12% 개선`하고 GPT-3과 같은 `500배 더 큰 모델`에서 `경쟁력 있는 퓨샷 성능`을 산출함을 보여줍니다.

---

### Dear my Friends.
> 1.기존 LMs 성능 좋지, 근데 모델 훈련시키기도 또 그걸 서빙하기에는 파라미터 너무 크잖아? 파라미터 적으면 똥이고 무조건 크면 장땡 이잖아.. 

> 2. 그래서 우리가 EFL을 들고 왔다 이말이야. 기존 NLP task를 entailment하게 바꾸고 8개 예제로 미세조정하면 된다고.  

> 3. 대조 학습 기반 비지도학습 데이터 증강 효과도 볼 수 있고, 다국어 사용할때도 쉽게 확장되서 사용 할 수 있어 그리고 체계적인 평가(eval)방법으로 신뢰도도 좋다고 무려 여느 기존 SOTA보다 12% 좋고 GPT-3보다 500 작은 모델인데 성능은 비빌 수 있단 말이지.

---

# Introduction


