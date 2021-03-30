---
title: "[Pstage1] Day1. Data EDA"
subtitle: Image Classification, Exploratory Data Analysis
tags: [Image Classification, data EDA] 

---

Boostcamp Day 41. 2021-03-29.
DAY41 TIL

# Data EDA

### Contents
- 목표/행동/회고

<br>

## 1. 오늘의 학습목표
강의에서 언급한 것 처럼 컴퍼티션 데이터를 가지고 스스로 EDA를 해보고 Notebook을 만들어 보세요!  
아무런 베이스 코드 없이 주어진 데이터로 어떻게 분석 결과를 만들어 가야 할 지 당황스러울 수도 있을것 같습니다.   

하지만, 강의에서 언급한 대로 무엇이든지 좋습니다.  아래의 Further Reading을 참고해서 혹시 다른 사람들은 어떻게 이미지데이터를 분석하는지 살펴보고, 자신만의 이미지분류 EDA 노트북을 만들어 보는 것도 좋겠습니다.

<br>

## 2. 무엇을 했는가
1. Baseline description에 대해서 이해하기
이번주 금요일에 제대로된 baseline code가 주어진다. 오늘 주어진 코드는 아주 간결한 tiny한 code만 주어지고 데이터에 대한 이해를 하는 단계였다.
우리가 사용하는 데이터 셋은 `마스크 착용여부`에 대한 img 데이터다. 아시아 남녀로 구분된 나이는 20대부터 70대 사이의 분포를 가지고 있다.  
마스크 착용 사진, 미착용 사진, 코스크 턱스크 등 이상하게 착용한 사진을 가지고 18가지 class로 구분하는것이다.

- train, eval 각각 csv file과 *.jpg 파일을 제공한다. eval은 이름과 다르게 test처럼 사용하면 될듯하다.  

- train.csv data의 columns를 `unique`함수로 파악해보니  
    - id : 2699
    - gender : 2
    - race : 1
    - age : 43
    - path : 2700

    > train.csv file은 non-null 즉 결측치가 없고 2700개라고 .info()의 결과로 확인했는데 하나가 없는게 신기했다. 왜일까?
    그리고 성별은 남녀로 2가지, 인종은 아시안으로 한가지, 나이는 20대부터 70대까지지만 43종류의 나이만 있는것으로 확인, `path`는 한 사람의 사진이 담긴 file의 path이다. 한 사람의 file에는 7장의 사진이 있다. 마스크 착용한 5장, 미착용 1장, 코스크턱스크 1장. 그래서 총 사진 갯수는 path * 7 이 총 사진의 양이라고 생각하면 될듯하다.

- eval.csv 는 column이 2개다. imageID와 ans.

- train/images는 path이름별로 7장의 사진이 들어가 있음.
    - 그런데 여기서 이상한점은 기존의 파일의 갯수의 2배가 들어가 있다. abc라는 file이 있으면 ._abc가 함께 존재하는데 
    - 라벨링 할때 이것들을 잘 제거해야 될듯하다.
    > 그래서 os.walk로 file directory를 탐색하며 filename의 앞에 ._가 존재하는 파일은 건너뛰기를 하고, 확장자가 .jpg인것만을 골라서 path와 filename을 담았지만
    문제가 있었다. 한사람의 파일당 사진이 7개라면 7 * 2700 = 18900이 나와야 하는데 18035가 나온다.


<br>

## 3. 아쉬운점
jupyter notebook의 코드를 두고 밑에 주석을 달면서 리뷰를 하면 더욱 편리할텐데 markdown으로 설명하려니 온전히 본인을 위한 글밖에 안되는거 같아 아쉽다.  

첫날인데도 불구하고 벌써 제출을 하신분들이 있었다.  
BaseLine을 그냥 제출하신분도 있고 labeling까지 마치고 어느정도 좋은 acc를 가지는 모델을 제출하신분도...  
경험을 하신분들은 눈에 금방금방 들어오시는거 같다.  
EDA를 안하고 바로 labeling을 하고 pretrained model 사용해서 제출하신분도 있었다.  
위축이 되지만 주어진 미션을 차근차근 해나간다는 마인드로 할것이다.  
첨부해주신 Kaggle Kernel을 보면서 다양한 EDA에 대해서 볼 수 있어서 좋았고 첫날 data EDA를 하느라 제출을 못했지만  
어서 빨리 제출해보고 싶다.  



## 해결할 의문들
> 1. path dir별로 사진이 7장씩 있는지 확인해 볼것.
> 2. train.csv에 id 중복이 있는거 같은데 한번 확인해볼것.
> 3. glob을 활용해서 읽어오는걸로 코드 짜보기.






<br><br>



## Reference

- bootcamp AI Tech pdf.  
- NAVER Connect Foundation.

