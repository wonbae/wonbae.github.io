boostcamp day 6. 2021-01-25.


# Numerical Python - Numpy
> 대용량의 `Matrix`와 `Vector`같은 과학수학 연산을 빠르게 계산해주는 Python Package.

---

### 목차
  1. Numpy
  2. Numpy 특징
  3. 설치
  4. 사용법
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

## 특징
- 반복문 없이 데이터 배열에 대한 처리를 지원.
- 일반 List에 비해 빠름.
- 선형대수와 관련된 다양한 기능을 제공함
- C,C++ 등의 언어와 통합 가능.

---

## 설치

본인이 가상환경을 사용하고 있으면 일단 거기로 이동해서 아래 설치 주문을 입력하셈.
아나콘다를 사용하여 설치하겠음. 아래는 Window 환경, Mac 환경도 동일 설치 명령어임.

```console
conda install numpy
```

주피터가 없으면 주피터 노트북도 설치해주시고

```console
conda install jupyter notebook
```

---

## 사용법

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

---

## Numpy Array vs Python List

넘파이 배열이 일반 파이썬 배열보다 빠름.
이유는 서로 저장 방식의 차이에 있습니다.
Python은 자주쓰는 -5 ~ 256 까지 숫자에 대해서 메모리의 특정 부분에 미리 할당시켜 놓음.
그래야 Interpreter언어가 보다 빨리 실행이 될 수 있기 때문.
이러다 보니, 숫자들을 들고 있는 배열은 각각의 숫자를 나란히 갖고 있는것이 아니라 서로 매핑된 주소값을 가지고 있음.
그러다 보니 옆에 나란히 놓여진 숫자들의 배열로 보이지만 알고보면 Interpreter가 열심히 매핑해서 찾고 그 다음에 값을 계산함.

하지만 Numpy는 미리 할당한 영역이 없이 그저 순수하게 입력된 배열의 값들을 메모리에 가지런히 갖다놓음. 그러면 메모리 참조하는 시간도 빠르고 (?) 결과적으로 계산속도가 빠름.

[참조 - 읽어보기](https://jakevdp.github.io/blog/2014/05/09/why-python-is-slow/)

---

## Array Creation

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

### Handling Shape
- reshape
  - Array의 shape의 크기를 변경함, element의 갯수는 동일
  ```python
  matrix = [[2,3,4,5],[6,7,8,9]]
  np.array(matrix).shape
  >>> (2,4)

  np.array(matrix).reshape(8,)
  >>> array([2,3,4,5,6,7,8,9])

  np.array(matrix).reshape(8,).shape
  >>>(8,)
  ```



  <br>

    ### Indexing & Slicing
    ### Creation Function
    ### Operation Functions
    ### Array Operations
    ### Comparisons
    ### Boolean & fancy Index
    ### Numpy Data I/O