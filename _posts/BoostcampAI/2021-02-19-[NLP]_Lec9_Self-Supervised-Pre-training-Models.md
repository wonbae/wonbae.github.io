---
title: "[NLP] Self-supervised Pre-Training Models"
tags:
    - Self-supervised Pre-Training Models
    - GPT-1
    - BERT
    - Transformer
    - DAY20 TIL
use_math: true
---

Boostcamp Day 20. 2021-02-19.


# Natural Language Processing (NLP) - Self-supervised Pre-Training Models

### Contents
-
- 

## Intro
자연어 처리 분야에 한 획을 그은 GPT-1과 BERT를 소개합니다.

GPT-1과 BERT는 Transfer Learning, Self-supervised Learning, Transformer를 사용했다는 공통점이 있습니다. 세가지의 강력한 무기를 이용해 대용량의 text를 학습한 모델을 target task에 적용해 거의 모든 기존 자연어처리 task를 압도하는 성능을 보여주었습니다. 세 가지의 키워드를 통해 두 모델을 자세히 알아봅니다.


# GPT-1
- it introduces special tokens, such as `<S>` / `<E>` / `$`, to achieve effective transfer learning durinf fine-tuning.
- it does not need to use additional task-specific architectures on top of transferred.

<img src="/assets/bcimg/NLP/gpt1.PNG">


<br><br>

# BERT
- 가장 널리 쓰이는 pre-training model
- Learn through masked language modeling task.
- Use large-scale data and large-scale model.

- Motivation
    - Language models only use left context or right context, but language understand bi-directional
        - 앞쪽 아님 바로 뒷쪽만 보고 예측하는건 한계가 있다.
    - if we use bi-directional language model?
        - problem : words can "see themselves" (cheating) int a bi-directional encoder.

## BERT : Next Sentence Prediction
- binary classification.
- To learn the relationships among sentences, predict whether Sentence B is an actual sentence that proceeds Sentence A, or a random sentence.

## BERT Summary
1. Model Architecture
    - BERT BASE: L = 12, H = 768, A = 12
    - BERT LARGE: L = 24, H = 1024, A = 16
2. Input Representation
    - WordPiece embeddings(30,000 WordPiece)
    - Learned positional embedding
    - [CLS]-Classification embedding
    - Packed sentence embedding[SEP]
    - Segment Embedding
3. Pre-training Tasks
    - Masked LM
    - Next Sentence Prediction

## BERT : Fine-Tuning Process
goon..


# BERT vs GPT-1
- Training-data size
    - GPT is trained on BookCorpus(800M words) ; 
    - BERT is trained on the BookCorpus and Wikipedia(2,500M words)

- Training special tokens during training
    - BERT learns [SEP],[CLS], and sentence A/B embedding during pre-training

- Batch size
    - BERT-128,000 words, GPT - 32,000 words

- Task-specific fine-tuing.
    - GPT uses the same learning rate of 5e-5 for all fine-tuning experiments; BERT chooses a task-specific fine-tuning learning rate.

    
<br><br>



## Further Reading
- [GPT-1](https://openai.com/blog/language-unsupervised/)
- [BERT : Pre-training of deep bidirectional transformers for language understanding, NAACL’19](https://arxiv.org/abs/1810.04805)
- [SQuAD: Stanford Question Answering Dataset](https://rajpurkar.github.io/SQuAD-explorer/)
- [SWAG: A Large-scale Adversarial Dataset for Grounded Commonsense Inference](https://leaderboard.allenai.org/swag/submissions/public)

## Further Question

- BERT의 Masked Language Model의 단점은 무엇이 있을까요? 사람이 실제로 언어를 배우는 방식과의 차이를 생각해보며 떠올려봅시다
    - 참고:  [XLNet: Generalized Auto-regressive Pre-training for Language Understanding](https://arxiv.org/abs/1906.08237)

<br><br>

## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.

