---
title: "Pandas 는 무엇인고?"
tags:
  - pandas
  - Python Data Analysis Library
  - 데이터분석
  - Python Library
  - 판다스
  - dataframe
  - series
use_math: true
---

Boostcamp Day 08. 2021-01-27.

# Python Data Analysis Library - Pandas

<img src="../../imgfile/bcimg/pandas/pandaslogo.png" width="40%" height="40%">

### Contents

- Definition
- Install
- Data Loading
- Series
- DataFrame
- selection & drop
- Dataframe Operations
- lambda, map, apply
- pandas Built-in Functions
    - describe
    - unique
    - sum
    - isnull
    - sort_values
    - Correlation & Covariance


<br><br>

# Definition
> 구조화된 데이터 처리를 지원하는 Python 라이브러리. Python계의 엑셀

- panel data의 줄임말로 pandas라고 함.
- 고성능 array계산 라이브러리인 `Numpy와 통합`하여, 강력한 `스프레드시트` 처리 기능을 제공.
- 인덱싱, 연산용 함수, 전처리 함수 등을 제공함.
- 데이터 처리 및 통계 분석을 위해 많이 사용.
- 흔히 Tabular Data(표)를 다룰 때 자주 사용.
  
<br>

- 특기 표 전체를 `Data Table`, Sample 라고 부름.
- 표의 윗부분 컬럼 부분을 `Attribute`, field, `feature`, column이라고 부름.
- 가로 행으로 있는 데이터들을 `Instance, tuple`, row 라고 부름.
- 컬럼 기준으로 세로로 있는 데이터들을 Feature vector라고 부름.

<br><br>

# Install
가상환경이 없으면 아래처럼 가상환경 생성 하시고
```bash
conda create -n 가상환경이름 python=3.8     
activate 가상환경이름        
conda install pandas
```

있으시다면 바로 가상환경 실행 후 아나콘다 사용해서 설치
```bash
activate 가상환경이름
conda install pandas
```

<br><br>

# Data Loading
csv 파일을 불러오는 방법이다. 이를 데이터 로딩이라고 부름.

```Python
import pandas as pd
data_url = 'https://archive.ics.uci.edu/ml/machine-learning-databases/housing/housing.data'
df_data = pd.read_csv(data_url, sep='\s+', header = None)   #csv 타입 데이터로드, separate는 빈공간으로 지정, 컬럼은 없음
df_data.head()      #처음 5줄 불러옴
```

이렇게 하면 컬럼은 비어있지만, 데이터를 불러오는거에 성공한것.

<br><br>

# Series
> DataFrame 중 `하나의 Column`에 해당하는 데이터의 `모음 Object`를 말함. 즉, `컬럼 벡터를 표현하는 object`라고 생각하면 됨.
<br>
위의 테이블로 예를 들자면, AGE라는 컬럼 밑으로 주루룩 있는 데이터들을 Series라고 함.
DataFrame은 Data Table 전체를 포함하는 Object이다.  
`시리즈가 모여서 데이터프레임을 구성`한다고 보면 됨.

- numpy.ndarray의 subclass이다. 즉, ndarray와 거의 같다고 보면된다.
- 어떤 타입이든 시리즈에 입력가능.
- Index가 정렬될 필요는 없고 자동정렬은 아니다. 즉, Index를 맘대로 변경 가능.
- 중복을 허용한다.  
 
 <br>

## 시리즈 출력해보기, 컬럼 변경해보기
```python
from pandas import Series, DataFrame
import pandas as pd
import numpy as np

list_data = [1, 2, 3, 4, 5]
example_obj = Series(data=list_data)
example_obj

# 이렇게 하면 출력 값이 Index는 0부터 시작하는 숫자가 임의로 들어가고

list_name = ["a", "b", "c", "d", "e"]
example_obj = Series(data=list_data, index=list_name)
example_obj

#이렇게 해주면 Index 값에 abcd가 들어간다.

example_obj.index           # index(['a','b','c','d','e']) 가 출력됨
example_obj.values          # array([1,2,3,4,5]) 가 출력됨
type(example_obj.values)    # numpy.ndarray 가 출력됨

```

어떤 타입이든 시리즈에 입력가능하니깐 이것도 된다.

```python
dict_data = {"a": 1, "b": 2, "c": 3, "d": 4, "e": 5}
example_obj = Series(dict_data, dtype=np.float32, name="example_data")
example_obj

# 이건 dict_data가 Index, value 쌍으로 이뤄져서 위에와 똑같이 나옴.
```
또한 List나 Dict 다루듯이 Key 값으로 접근하는것도 가능, 값을 바꾸는 것도 가능.

```python
example_obj["a"]    # 1.0

example_obj = example_obj.astype(float)
example_obj["a"] = 3.2
example_obj
```
그리고 true false도 argument로 가능.
```python
cond = example_obj > 2
example_obj[cond]
# or
example_obj[example_obj > 2]
```
그리고 시리즈에 정수를 곱해주면 브로드캐스팅처럼 모든 값에 곱해짐.
```python
example_obj * 2
# 각 vector에 전부 곱해짐
```
그리고 마지막으로 시리즈는 Index 값 기준으로  시리즈를 생성함. 무슨말이냐면 값이든 인덱스든 입력이 될텐데, 이때 Index값이 입력값보다 많으면 일단 Index 갯수만큼 시리즈를 만들고 값이 빈 곳에는 NaN(Not a Number)값이 들어간다.

<br><br>

# DataFrame
> Series가 모여 만들어진 Data Table (기본 2차원)

- Numpy array라고 보면됨.
- 각 컬럼들은 각기 다른 데이터 타입을 가질 수 있음. 어떤건 str 어떤건 int, float.
- 2차원 배열처럼 raw 와 column 으로 Indexing함.
- 가변성, 값을 넣을 수도, 지울수도 있는 변화가 가능하단 뜻.

<br>

쫌 살펴보자

```python 
from pandas import Series, DataFrame
import pandas as pd
import numpy as np

# Example from - https://chrisalbon.com/python/pandas_map_values_to_values.html
raw_data = {
    "first_name": ["Jason", "Molly", "Tina", "Jake", "Amy"],
    "last_name": ["Miller", "Jacobson", "Ali", "Milner", "Cooze"],
    "age": [42, 52, 36, 24, 73],
    "city": ["San Francisco", "Baltimore", "Miami", "Douglas", "Boston"],
}
df = pd.DataFrame(raw_data, columns=["first_name", "last_name", "age", "city"])
df
```

이런 식으로 데이터프레임을 만듬. rawdata에 각 Index 값과 vector값들이 들어가 있는게 보인다.

dataframe으로 컬럼을 골라서 볼 수 잇고 시리즈와 마찬가지로 Index가 더 많을 경우 Feature vector에는 NaN값이 들어감.

```python
DataFrame(raw_data, columns=["age", "city"])    # 컬럼 선택
DataFrame(raw_data, columns=["first_name", "last_name", "age", "city", "debt"])  # 컬럼추가
```

- `loc` -> Index Location
    - Index 이름이라고 생각하면됨.
- `iloc` -> Index Position
    - Index가 몇번째인지 순서, number라고 생각하면됨.

```python
s = pd.Series(np.nan, index = [45,46,47,48,1,2,3])
s.loc[:3]   #3이 끝에 있으니깐 끝까지 출력함.
s.iloc[:3]  #3번째 까지 출력하라는 뜻.
```

<br><br>

# selection & drop

## selection with column names
한개의 컬럼 선택시
```python
df['account'].head(3)
```
1개 이상의 컬럼 선택시
```python
df[['location', 'date', 'city']].head(3)
```
대괄호 쌍 하나 더 붙여줘야함.

<br>

## selection with Index number
컬럼 이름 없이 Index number 사용하면 row 기준으로 3개의 Instance를 보여줌.
```python
df[:3]
```
컬럼 이름과 함께 index 사용시 해당 컬럼의 feature vector만 보여줌.
```python
df['account'][:3]
```
Boolean index도 가능.
```python
budget_serires = df["budget"]
budget_serires[budget_serires > 20000]  #20000 이상만 보여줌.
```
- axis
    - axis가 0이면 raw, 1이면 column 의 줄을 삭제

<br><br>


# Dataframe Operations

- Serires Operation
    - Index 기준으로 연산 수행, 겹치는 Index 없을 경우 NaN값 반환.
- DataFrame Operation
    - Column과 Index 모두 고려해서 딱 맞아야 연산 (add, sub, div, mul)
    - 그래서 Option을 `fill_value`
     같은걸 줘서 NaN 대신에 다른값 삽입 가능.
- Serires + DataFrame
    ```python
    df.add(serires, axis=0)
    # 이런식으로 하면 axis 기준으로 Broadcasting이 실행됨. axis = 0 이면 row 1이면 컬럼별로
    ```

<br><br>

# pandas Built-in Functions
## describe
- Numeric type 데이터의 요약 정보를 보여줌.
## unique
- Series data의 유일한 값을 list로 반환.
## sum
- column, row값의 연산을 지원, axis로 선택.
- sub, mean, min, max, count, median, mad, var 등
## isnull
- column or row 값이 NaN인지 true false로 보여줌. 주로 sum()과 함께 사용해서 Index별 결측치가 있는지 확인함.
## sort_values
- column 값을 기준으로 데이터를 sorting.
## Correlation & Covariance
- 상관계수와 공분산을 구하는 함수
- corr(), cov(), corrwith()
