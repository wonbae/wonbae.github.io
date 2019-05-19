https://towardsdatascience.com/6-different-ways-to-compensate-for-missing-values-data-imputation-with-examples-6022d9ca0779

# 결측치,이상치 (Missing Values) 6가지 처리 방법(Imputation)
> Popular strategies to statistically impute missing values in a dataset


- Mssing completely at random(MCAR)
- Mssing at random(MAR)
- Not missing at random(NMAR)



## 1. Do Nothing
  > 아무런 처리도 하지 않는 것.
  
  
## 2. Imputation Using(Mean/Median) Values
  > NaN 결측치를 해당 컬럼(Feature, Columns)의 NaN을 제외한 나머지값의 `평균(Mean)` or `중앙값(Median)`을 통해 대체하는 방법
  
#### 장점:
  - 쉽고 빠름(easy and fast)
  - 비교적 적은 숫자형 데이터에서는 좋음(Works well with samll numerical datasets)

#### 단점:
  - 설명변수(Features)간의 상관관계(Correlations)는 고려하지 않고 해당 컬럼, 결측치가 존재하는 해당 컬럼 하나에서만 동작
    - (Doesn't factor the correlations between features. It only works on the column level)
  - 연속형, Numerical(숫자형)이 아닌 이산형, 문자와 같은 카테고리에서는 (Ex, Female/male) 개 그지같은 결과가 생김(쓰지말란말)
  - 그다지 정확하지 않다
  - 결측치를 채워 넣는 과정(Imputations)에서 설명력이 떨어진다(?) 불확실하고 처리에 대해서 잘 설명하지 못한다(라고 해석됨)
    - (Doesn’t account for the uncertainty in the imputations.)
  
  
  
## 3. Imputation Using(Most Frequent) or(Zero/Constant) Values
  > String or Numerical 데이터에 대해서도 사용가능한 방법, 각 컬럼에서 가장 많이 사용되는(등장하는) 값으로 대체하는 방법
  
#### `Most Frequent`
  각 컬럼에서 가장 많이 사용되는(등장하는) 값으로 대체하는 방법
  
#### 장점:
  - Categorical features(범주형 설명변수(컬럼))에 대해서도 잘 됨

#### 단점:
  - Data를 외곡시킬 수 있다. (안그래도 많이 쓰이는데 더 많이 쓰이는 걸로 나타남)
    - (It can introduce `bias` in the data), (bias : 지표, 척도, 기울기, verb : 한쪽으로 치우치게 하다)
  - 이것 또한 각 설명변수(Features)사이의 상관관계(Correlations)을 고려하지 않는다
  
  
#### `Zero or Constant`
  `0`으로 대체하거나 하나의 값으로 일정하게 넣어 주는 방법
  

  
## 4. Imputation Using K-NN
  > 아무런 처리도 하지 않는 것.
  
  
## 5. Imputation Using Multivariate Imputation by Chained Equation(MICE)
  > 
  
  
  
## 1. Do Nothing
  > 아무런 처리도 하지 않는 것.
