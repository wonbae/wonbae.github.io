---
title: "[Pstage1] Day2. 전처리 Dataset, Augmentation"
subtitle: Image Classification, Augmentation
tags: [Augmentation, torchvision] 

---

Boostcamp Day 42. 2021-03-30.
DAY42 TIL

### Contents
- 목표/행동/회고

<br>

## 1. 오늘의 학습목표
- 데이터 전처리의 개념에 대해서 설명합니다. 컴퍼티션의 경우 어느 정도 정제된 데이터가 주어지지만, 앞으로 우리가 만나게 될 데이터는 cleaning 되어 있지 않는 경우가 많기 때문에 사전에 여러가지 작업들이 필요합니다. 이미지 데이터는 비교적 전처리할 거리가 그렇게 많지는 않지만 정형데이터나 텍스트 데이터의 경우는 상상을 초월하는 전처리를 경험하시게 될거.
그리고, Generalization(일반화) 관점에서 생각해 볼 수 있는 몇 가지 Skill를 다룹니다.
 의사결정을 하는데에는 문제를 어떻게 정의했느냐가 매우 중요한 요소로 활용될 수 있습니다.  


- Vanilla 데이터를 가지고 Dataset을 구성한 다음 모델에 빠르고, 효율적으로 Feeding 하기 위해 알아야 할 것들에 대해서 다룹니다. 강의에서 Data Feeding이라고 말하는 것의 개념과, 실제로 이것을 제대로 하지 않았을 때 어떤 일들이 일어날 수 있는지 알아보겠습니다.  
그리고, 파이토치에서 torch.utils.data에 있는 Dataset, DataLoader에 대한 설명과, 그 차이를 다뤄보겠습니다.


- 1. 주어진 바닐라 데이터를 가지고 이미지와 해당하는 클래스 Label (18개의 클래스 중 하나)을 생성할 수 있는 Pytorch Dataset Class를 직접 생성해보세요.
만약 이런 과정을 직접 만들어보는게 처음이시라면 생각보다 시간이 오래 걸릴 것이라 예상합니다. 하지만 이 과정은 캠퍼분들 스스로 반드시 해보길 권장합니다. 
18개의 클래스를 만드셨다면, 그 타겟 클래스의 분포도 다시 한번 확인해보면 좋겠습니다.  


- 2. 강의때 보여드렸던 torchvision에 내장된 여러 Augmentation 함수와 albumentation 라이브러리의 여러 transform 기법을 적용해보세요. 적용해 보신 뒤에 실제로 어떻게 변환되어 나오는지 확인해보세요. 아마 plot형태로 그려서 확인해야 할거에요.
그리고 이러한 Transforms를  추가한 Dataset이 과연 어느 정도의 성능을 가지는지 체크해보세요. 혹여 너무 무거운 프로세스라면 생각보다 느리게 동작하겠죠? 


<br>

## 2. 무엇을 했는가
### 수업
- 주제를 깊게 관찰하여 다양한 기법들을 적용하면 다양성을 가질 수 있다는 것을 명심하고 `실험으로 증명하자`. 무조건이란건 없다.
- 데이터 전처리는 모델링에 앞서서 도메인에 맞게 데이터를 변형하는 과정이다. 마치 모델이라는 동물에 먹이를 주듯이
- Dataset과 DataLoader는 다르다. 
    - `Dataset`은 vanilla데이터를 원하는 형태로 출력해주는 클래스
    - `DataLoader`는 Dataset을 더 효율적으로 사용하기 위함

### 피어세션
- 이야기를 많이 해서 좋았다.
- 어제 data EDA로 찾은 id값 중복과 jpg외의 확장자가 있다는 사실을 공유했고 나름 작은 도움(?)을 드렸다.
- Augmentation에 대해서 이야기를 하다가 데이터를 늘리기 위해서 Augmentation을 하는것도 맞지만, 비단 그것뿐만이 아니라 Generalization(일반화)를 하는것이 목표라는 것을 서로 이야기 했다.
- 연령을 파악하는것에 대해서 이야기 했다. 연령의 경계에 있는 애매한 나이의 데이터는 오히려 분류모델에 안좋다는 의견이 있었다. 그리고 마스크 착용 여부와 연령, 성별 등을 파악해야 하니 각 task별로 모델을 각각 개별적으로 만들어서 따로 학습시키고 어셈블하는건 어떤가 하는 의견도 있었다. 정말 그럴듯한데 이래도 되는걸까? 나중에 해봐야 겠다.

### 개인
- 어제는 중복이 있다는 사실만 알았지 어떤 row인지 찾아보지 않았는데 2가지 방법으로 찾아보았다.
- `duplicated` fuction의 keep parameter로 중복을 모두 보여줄것인지 뒤에꺼 혹은 앞에꺼를 선택할 수 있다.
```python
for id, flag in enumerate(train_csv['id'].duplicated(keep=False)):
    if flag == True:
        dup = train_csv.iloc[id]
        print(dup)
        print('\n')
```
object형태로 해당 id의 row가 출력된다.

```python
df_dup = pd.DataFrame(train_csv, columns=['id'])

duplicate_id = df_dup[df_dup.duplicated(keep=False)]
duplicate_id
```
DataFrame형태로 중복인 id값만 나온다.

- 제공해주신 EDA자료를 반밖에 못봤다. 비슷한 부분도 있었고 전혀 처음보는 부분도 있었다. Pandas를 다루는 연습이 절실하다.
- torch.utils.data를 이해하는데에 시간을 많이 들었다. 어떤 파라미터가 transform시키는지 글로만 이해했다. 근데 Albumentations가 성능이 압도적으로 좋아서 저 library를 사용해야 할꺼같다.

<br>

## 3. 아쉬운점

- 뭐든 많이 시도해보고 싶은데 생각보다 빠르게 진행이 안되서 답답하다. 모르는게 참 많다는 생각이든다.
- 


## 내일 할 것
- albumentation사용해서 transform형태 변화를 plot으로 그려보기.






<br><br>



## Reference

- bootcamp AI Tech pdf.  
- NAVER Connect Foundation.

