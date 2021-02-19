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
GPT-1과 BERT 이후 등장한 다양한 self-supervised pre-training 모델들에 대해 알아봅니다.

GPT-1과 BERT 이후 pre-training task, 학습 데이터, self-attention, parameter 수 등에 있어서 여러가지 개선된 모델들이 등장했습니다. GPT 시리즈가 2와 3로 이어지면서 일부 데이터셋/task에 대해서는 사람보다 더 뛰어난 작문 능력을 보여주기도 합니다. 이로 인해, model size 만능론이 등장하며 resource가 부족한 많은 연구자들을 슬프게 만들기도 했습니다. 다른 연구 방향으로 transformer의 parameter를 조금 더 효율적으로 활용하고 더 나은 architecture/pre-training task를 찾고자 하는 ALBERT와 ELECTRA에 대해서 알아봅니다. 두 모델 모두 풍부한 실험과 명확한 motivation으로 많은 연구자들의 관심을 받은 논문입니다.

위에서 설명드린 연구방향과는 또 다른 연구 흐름으로 경량화 모델/사전 학습 언어 모델을 보완하기 위한 지식 그래프 integration에 대해 소개한 논문들을 간략하게나마 알아봅니다. 관심 있으신 분들은 이후 진행될 경량화 모델 수업과 그래프 수업을 유심히 들어주시면 좋을 것 같습니다
    
<br><br>

# GPT-2
> Language Models are Unsupervised Multi-task Learners
- jsut a really big transformer LM
- Trained on 40GB of text
    - Quite a bit of effort going into makin sure the dataset is good quality
    - Take webpages from reddit links with high karma.

- Language model can perform down-stream tasks in a zero-shot setting - without any parameter or architecture modification.

## GPT-2 : Motivaiton
- The Natural Language Decathlon : Multitask Learning as Question Answering.

## GPT-2 : Datasets
- 큰 특징중 하나가 Reddit에 올라온 질문에 대한 답변을 참고할 뿐만 아니라 답글에 담긴 Link까지 타고들어가 link의 글의 내용을 신뢰해서 data set에 추가한다. 신뢰성은 up-vote가 3개이상이면 괜찮다 생각하고 들고옴.

## GPT-2 : Model
- Modification
    - Layer normalization was moved to the input of each sub-block, similar to a pre-activation residual network.
    - Additional layer normalizaiton was added after the final self-attention block.
    - Scaled the weights of residual layer at initializaiton by a factor of $1 \over \sqrt n$ where $n$ is the number of residual layer. 
        - 위쪽의 layer로 갈수록 영향력을 줄여주거나 높여주거나.

<br><br>

# GPT-3
> Language Models are Few-Shot Learners.
- Scaling up language models greatly improves task-agnostic, few-shot performance.
- An autoregressive language model with 175 billion parameters in the few-shot setting
- 96 Attention layers, Batch size of 3.2M
-GPT-2와 다르게 Self-Attention Block을 쌓아서 비교할수 없을정도로 더 많은 parameter를 만듬.


<br><br>

# ALBERT : A Lite BERT
Self-supervised Learning of Language Representations.

- Is having better NLP models as easy as having larger models?
    - Obstacles
        - Memory Limitation
        - Training Speed
    - Solutions
        - Factorized Embedding Parameterization
        - Cross-layer Parameter Sharing
        - (For Performace)Sentence Order Prediction


<br><br>

# ELECTRA
> Efficiently Learning and Encoder that Classifies Token Replacements Accurately.

- Learn to distingush real input tokens from plausible but synthetically generated replacements.
- Pre-training text encoders as discriminators rather than generators.
- Discriminator is the main networks for pre-traing.






## Further Reading
- How to Build OpenAI’s GPT-2: “ The AI That Was Too Dangerous to Release”
GPT-2
- Illustrated Transformer
- ALBERT: A Lite BERT for Self-supervised Learning of Language Representations, ICLR’20
- ELECTRA: Pre-training Text Encoders as Discriminators Rather Than Generators, ICLR’20
- DistillBERT, a distilled version of BERT: smaller, faster, cheaper and lighter, NeurIPS Workshop'19
- TinyBERT: Distilling BERT for Natural Language Understanding, Findings of EMNLP’20
- ERNIE: Enhanced Language Representation with Informative Entities, ACL'19
- KagNet: Knowledge-Aware Graph Networks for Commonsense Reasoning, EMNLP'19



<br><br>

## Reference

- bootcamp AI Tech pdf  .
- NAVER Connect Foundation.

