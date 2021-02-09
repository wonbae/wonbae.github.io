boostcamp day 06. 2021-01-25.

# Numerical Python - Numpy
> 대용량의 `Matrix`와 `Vector`같은 과학수학 연산을 빠르게 계산해주는 Python Package.

---

### Contents
  1. Numpy
  2. Numpy 특징
  3. 설치
  4. Numpy Array vs Python List
  - Array Creation  
  - Handling Shape  
  - Indexing & Slicing  
  - Creation Function  
  - Operation Functions  
  - Array Operations  
  - Comparisons  
  - Boolean & fancy Index  
  - Numpy Data I/O  

---

# 특징
- 반복문 없이 데이터 배열에 대한 처리를 지원.
- 일반 List에 비해 빠름.
- 선형대수와 관련된 다양한 기능을 제공함
- C,C++ 등의 언어와 통합 가능.

---

# Install 설치

본인이 가상환경을 사용하고 있으면 일단 거기로 이동해서 아래 설치 주문을 입력하셈.
아나콘다를 사용하여 설치하겠음. 아래는 Window 환경, Mac 환경도 동일 설치 명령어임.

```console
conda install numpy
```

주피터가 없으면 주피터 노트북도 설치해주시고

```console
conda install jupyter notebook
```

# 사용법

이제 시작해 봅시다

```Python
import numpy as np
```

- Numpy 호출 방법입니다. import 해야 numpy 패키지를 불러서 쓸 수 있고
- alias(별칭)을 np를 주로 사용합니다. 국룰 입니다. 아니, 세계룰! 왜냐? 타자치기 귀찮고 가독성이 좋으니깐.

```Python
test = np.array([1,5,3,6], float)
print(test)
type(test[3])
```
> array([1., 5., 3., 6.])
> numpy.float64

- np.array합수를 활용해서 배열을 생성하고
- `List와 가장 큰 차이점`은 하나의 데이터 Type만 배열에 넣을 수 있음.
  - List는 str 이나 int형 자료구조가 혼합되어 사용가능 했음.
- 그리고 `Dynamic Typing NOT Supported` 임
  - 그래서 저 배열 선언 부분에 float라고 자료형을 넣어 준거임. 명시해줘야함.

<br><br>

# Numpy Array vs Python List

넘파이 배열이 일반 파이썬 배열보다 빠름.
이유는 서로 저장 방식의 차이에 있습니다.
Python은 자주쓰는 -5 ~ 256 까지 숫자에 대해서 메모리의 특정 부분에 미리 할당시켜 놓음.
그래야 Interpreter언어가 보다 빨리 실행이 될 수 있기 때문.
이러다 보니, 숫자들을 들고 있는 배열은 각각의 숫자를 나란히 갖고 있는것이 아니라 서로 매핑된 주소값을 가지고 있음.
그러다 보니 옆에 나란히 놓여진 숫자들의 배열로 보이지만 알고보면 Interpreter가 열심히 매핑해서 찾고 그 다음에 값을 계산함.

하지만 Numpy는 미리 할당한 영역이 없이 그저 순수하게 입력된 배열의 값들을 메모리에 가지런히 갖다놓음. 그러면 메모리 참조하는 시간도 빠르고 (?) 결과적으로 계산속도가 빠름.

[참조 - 읽어보기](https://jakevdp.github.io/blog/2014/05/09/why-python-is-slow/)

---

<br>

# Array Creation

```Python
test_array = np.array([1,4,5,"8"], float)     # String type 이여도 형변환 될까?
print(test_array)
print(type(test_array[3]))                    # 네, 됩니다. 이부분에서 확인가능하죠
print(test_array.dtype)                       # Array의 전체의 데이터 Type을 반환함
print(test_array.shape)                       # Array의 Shape을 반환함
```

> array([1., 4., 5., 8.])
numpy.float64
dtype('float64')
(4,)


Rank | Name | Example
---|:---:|:---:
0 | Scalar | 7
1 | Vector | [10, 10]
2 | Matrix | [[10,10],[15,15]]
3 | 3-tensor | [[[1, 5, 9], [2,6,10]], [[3, 7, 11], [4, 8, 12]]]
n | n-tensor | 

- 3rd order tensor Shape

```Python
tensor = [[[1,2,3,4],[1,2,3,4],[1,2,3,4]],
          [[1,2,3,4],[1,2,3,4],[1,2,3,4]],
          [[1,2,3,4],[1,2,3,4],[1,2,3,4]],
          [[1,2,3,4],[1,2,3,4],[1,2,3,4]],
          [[1,2,3,4],[1,2,3,4],[1,2,3,4]]]
np.array(tensor, int).shape
```
> (5, 3, 4)

솔직히 이거 햇갈린다. 아마 실수할꺼 같은데 주의해서 보자.
`(dense, row, column)` 으로 생각하면 그나마 안헛갈릴듯함.

<br> 

---

# Handling Shape
## `reshape`
    - Array의 shape의 크기를 변경함, element의 갯수는 동일
  ```python
  matrix = [[2,3,4,5],[6,7,8,9]]
  np.array(matrix).shape
  >>> (2,4)

  np.array(matrix).reshape(8,)
  >>> array([2,3,4,5,6,7,8,9])

  np.array(matrix).reshape(8,).shape
  >>> (8,)
  ```

  - `-1` : Size 를 기반으로 row 개수 선정
  ```python
  np.array(matrix).reshape(2,4).shape
  >>> (2,4)
  np.array(matrix).reshape(-1,2).shape
  >>> (4,2)
  ```

  > 원래의 값(matrix)이나 구조는 건드리지 않고 변형된 형태를 반환하는 형식이다.
  ```python
  matrix = [[1,2,3,4,5],[5,6,7,8,9]]
  np.array(matrix).shape
  >>> (2,5)

  np.array(matrix).reshape(5,2)
  >>> array([[1,2],
            [3,4],
            [5,5],
            [6,7],
            [8,9]])
  np.array(matrix).reshape(5,2).shape
  >>> (5,2)

  np.array(matrix).shape
  >>> (2,5)
  ``` 

  - 3차원으로 reshape 가능.
  ```python
  matrix = [[1,2,3,4],[5,6,7,8]]
  np.array(matrix).reshape(2,2,2)

  >>> array([[[1,2],
              3,4]],
              
              [[1,2],
              5,8]]])

  np.array(matrix).reshape(2,2,2).shape
  >>> (2,2,2)
  ```

  <br>

## `flatten`
> 다차원 array를 1차원 array로 변환.

(2,2)차원이든 (2,2,4) 차원이든 그냥 일자로 피는거. 

```python
matrix = [[[1,2,3,4], [1,2,5,8]], [[1,2,3,4], [1,2,5,8]]]
np.array(matrix).flatten()

>>> array([1,2,3,4,1,2,5,8,1,2,3,4,1,2,5,8])
```

<br>


# Indexing & Slicing
## Indexing for numpy array
- list와 달리 이차원 배열에서 `[0,0]` 표기법을 제공함.
- matrix일 경우 앞은 row 뒤는 column을 의미.
```python
a = np.array([[1,2,3], [4.5, 5, 6]], int)
print(a)
print(a[0,0])
print(a[0][0])

a[0,0] = 12     # matrix 0,0에 12 할당. 이러면 [0,0]값이 바뀜.
print(a)
a[0][0] = 5
print(a)
```

## Slicing for numpy array
- list와 달리 행과 열 부분을 나눠서 slicing이 가능함.
  - `쉽표 : ,`를 기준으로 행과 열로 나뉨.
  - 쉽표가 없을 경우가 좀 햇갈리는데. `row` 라고 생각하면됨.
- matrix의 부분 집합을 추출할 때 유용함.

```Python
a = np.array([[1,2,3,4,5], [6,7,8,9,10]], int)
a[:, 2:]
>>> array([[ 3,  4,  5],
            [ 8,  9, 10]])

a[1, 1:3]
>>> array([7, 8])

a[1:3]
>>> array([[ 6,  7,  8,  9, 10]])     # 1row ~ 2row의 전체

a[1:2]
>>> array([[ 6,  7,  8,  9, 10]])

a[0:2]
>>> array([[ 1,  2,  3,  4,  5],
            [ 6,  7,  8,  9, 10]])

a[:, 1:3]
>>> array([[2, 3],
           [7, 8]])

a[1, :2]
>>> array([6, 7])

a[:,::2]
>>> array([[ 1,  3,  5],
             [ 6,  8, 10]])

a[::2,::3]
>>> array([[1, 4]])
```

<br>

# Creation Function
## `arange`
- array의 범위를 지정하여, 값의 list를 생성하는 명령어.
- 파라미터를 3개 넣을 수 있는데 (시작, 끝, step)

```python
np.arange(5)            # list의 range와 같은 효과 0 ~ 4까지
>>> array([0,1,2,3,4])

np.arange(0, 3, 0.5)
>>> array([0, 0.5, 1, 1.5, 2, 2.5])

np.arange(10).reshape(2,5)
>>> array([[0, 1, 2, 3, 4],
            [5, 6, 7, 8, 9]])
```

## `ones, zeros and empty`
- `zeros`
  - 0으로 가득찬 ndarray생성.
  - np.zeros(shape, dtype, order)
  ```python
  np.zeros(shape=(10,), dtype=np.int8)
  >>> array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0], dtype=int8)

  np.zeros((2,5))                   # 2 by 5 zero matrix 생성
  >>> array([[0., 0., 0., 0., 0.],    
             [0., 0., 0., 0., 0.]])
  ```

- `ones`
  - 1로 가득찬 ndarray생성
  - np.ones(shape, dtype, order)
  ```python
  np.ones(shape=(10,), dtype=np.int8)
  >>> array([1, 1, 1, 1, 1, 1, 1, 1, 1, 1], dtype=int8)  

  np.ones((2,5))
  >>> array([[1., 1., 1., 1., 1.],
              [1., 1., 1., 1., 1.]])
  ```

- `empty`
  - shape만 주어지고 비어있는 ndarray 생성
  - Memory initialization이 되지 않음
  ```python
  np.empty(shape=(10,), dtype=np.int8)
  >>> array([1, 1, 1, 1, 1, 1, 1, 1, 1, 1], dtype=int8)

  np.empty((3,5))
  >>> array([[6.23042070e-307, 4.67296746e-307, 1.69121096e-306,
              1.15711310e-306, 7.56587585e-307],
            [1.37961302e-306, 1.05699242e-307, 8.01097889e-307,
              1.78020169e-306, 7.56601165e-307],
            [1.02359984e-306, 1.33510679e-306, 2.22522597e-306,
              8.01097889e-307, 0.00000000e+000]])
  ```

## something_like
- 기존의 ndarray의 shape 크기 만큼, 1,0 또는 empty array를 반환.
```python
test = np.arange(30).reshape(5,6)
np.ones_like(test)
np.zeros_like(test)
np.empty_like(test)
```

## `identity`
- 단위행렬을 생성.
- n -> number of rows
```python
np.identity(n=3, dtype=np.int8)
np.identity(5)
```

## `eye`
- 대각선이 1인 행렬, k값의 시작 index의 변경이 가능

```python
np.eye(3)
>>> array([[1., 0., 0.],
            [0., 1., 0.],
            [0., 0., 1.]])

np.eye(3,5,k=2)
>>> array([[0., 0., 1., 0., 0.],
            [0., 0., 0., 1., 0.],
            [0., 0., 0., 0., 1.]])

np.eye(N=3, M=5, dtype=np.int8)
>>> array([[1, 0, 0, 0, 0],
            [0, 1, 0, 0, 0],
            [0, 0, 1, 0, 0]], dtype=int8)
```

## `diag`
- 대각 행렬의 값만을 추출.
```python
matrix = np.arange(9).reshape(3,3)
matrix
>>> array([[0, 1, 2],
          [3, 4, 5],
          [6, 7, 8]])

np.diag(matrix)

>>> array([0,4,8])

np.diag(matrix, k=1)    # k -> start index

>>> array([1,5])
```

## `random sampling`
- 데이터 분포에 따른 sampling으로 array를 생성.
```python
np.random.uniform(0,1,10).reshape(2,5)    # 균등분포
>>> array([[0.91993324, 0.03996477, 0.99758625, 0.61466441, 0.47749502],
          [0.0654897 , 0.6740845 , 0.01977392, 0.0359981 , 0.0324615 ]])

np.random.normal(0,1,10).reshape(2,5)     # 정규분포
>>> array([[ 0.76108207, -0.96711577,  0.74295074, -0.31169504,  0.59968418],
          [ 0.65314334, -0.31441779,  0.3354662 ,  0.04795257, -0.13263159]])
```

<br>

# Operation Functions
## `sum`
- ndarray의 element들 간의 합을 구함, list의 sum 기능과 동일.

## `axis`
- 모든 operation function을 실행할 때 기준이 되는 dimension 축.
- 이게 햇갈리기 쉬운데, axis = 0은 위에서 아래로 꽂고(컬럼별로), 1은 왼쪽에서 오른쪽으로(row) 꼬챙이 끼운다고 생각하면됨. 

```python
test_array = np.arange(1, 13).reshape(3,4)
test_array

>>>    array([[ 1,  2,  3,  4],
              [ 5,  6,  7,  8],
              [ 9, 10, 11, 12]])


test_array.sum(axis=1), test_array.sum(axis=0)

>>> (array([10, 26, 42]), array([15, 18, 21, 24]))
```

- 3차원이 되었을 때(Tensor)는 (depth, row, column) 이 순서대로 axis 0, 1, 2 이다.이게 무슨 말이냐면 depth라고 적은건 우리가 흔히 생각하는 z 축을 말하는 거임. 특이하게 맨 앞에 들어간다는거.

![tensor-axis](../../imgfile/bcimg/numpy/tensor-axis.png)


## `mean & std`
- ndarray의 element들 간의 `평균` 또는 `표준 편차`를 반환.
```python
test_array = np.arange(1,13).reshape(3,4)
test_array
>>> array([[ 1,  2,  3,  4],
           [ 5,  6,  7,  8],
           [ 9, 10, 11, 12]])

test_array.mean(), test_array.mean(axis=0)
>>> (6.5, array([5., 6., 7., 8.]))


test_array.std(), test_array.std(axis=0)
>>> (3.452052529534663, array([3.26598632, 3.26598632, 3.26598632, 3.26598632]))
```

## `mathematical functions`
- np.something 형식으로 호출.
- exponential : exp, expm1, exp2, log, log10, log1p, log2, power, sqrt
- trigonometric : sin, cos, tan, acsin, arccos, atctan
- hyperbolic : sinh, cosh, tanh, acsinh, arccosh, atctanh

## `concatenate`
- numpy array를 합치는(붙이는) 함수
```python
a = np.array([1,2,3])
b = np.array([4,5,6])
np.vstack((a,b))

>>> array([[1,2,3],
          [4,5,6]])
```
- `vstack`은 vertical  수직으로 서로 합치는거라고 보면됨.
- `hstack`은 horizental 수평으로 서로 합치는거.

```python
a = np.array([ [1], [2], [3]])
b = np.array([ [4], [5], [6]])
np.hstack((a,b))

>>> array([[1,4],
           [2,5],
           [3,6]])
```

- concatenate랑 axis를 사용할수도 있음.
- concatenate / axis=0
```python
a = np.array([[1,2,3]])
b = np.array([[4,5,6]])
np.concatenate( (a,b), axis=0)

>>> array([[1,2,3],
          [2,3,4]])
```

- concatenate / axis=1
```python
a = np.array([[1,2], [3,4]])
b = np.array([[5,6]])
np.concatenate( (a, b.T), axis=1)

>>> array([[1,2,5],
          [3,4,6]])
```


## Array Operations
## Comparisons
## Boolean & fancy Index
## Numpy Data I/O