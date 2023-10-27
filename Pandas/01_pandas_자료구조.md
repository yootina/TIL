# Pandas 기본 자료구조

## 개요
**관계형** 또는 **레이블이 된** 데이터로 쉽고 직관적 으로 작업할 수 있도록 설계되었고, 빠르고, 유연한 데이터 구조를 제공하는 Python 패키지입니다.

또한, 어떤 언어로도 사용할 수 있는 가장 **강력하고 유연한 오픈 소스 데이터 분석 / 조직 도구**입니다.

Pandas는 다음의 종류의 데이터에 적합한 분석 패키지입니다.

- SQL 테이블 또는 Excel 스프레드 시트에서와 같은 열과 행으로 이루어진 테이블 형식 데이터
- 정렬되고 정렬되지 않은 시계열 데이터
- 다른 형태의 관찰 / 통계 데이터 세트

## Pandas 공식 문서
공식 문서는 다음 링크에서 확인할 수 있습니다. <br/>
- [공식 도큐먼트](https://pandas.pydata.org/docs/reference/index.html).


## Pandas의 Alias(별명) 지정
pandas는 `pd`의 alias를 사용합니다.

```python
import pandas as pd

pd
```

## 1. 시리즈(Series)

Pandas의 Series는 1차원 배열로서 다음의 특징을 가집니다.

- 데이터를 담는 차원 배열 구조를 가집니다.
- 인덱스(index)를 사용 가능합니다.
- 데이터 타입을 가집니다. (dtype)

### 1-1. Series의 생성
Pandas의 Series는 1차원 배열로서 다음의 특징을 가집니다.

- 데이터를 담는 차원 배열 구조를 가집니다.
- 인덱스(index)를 사용 가능합니다.
- 데이터 타입을 가집니다. (dtype)

### - numpy array로 생성한 경우
```python
arr = np.arange(100, 105)
arr

array([100, 101, 102, 103, 104])
```
### - dtype을 지정한 경우
```python
#숫자들의 데이터를 효율적으로 관리하기 위해서
s = pd.Series(arr, dtype='int64')
s

0    100
1    101
2    102
3    103
4    104
dtype: int64
```

### - list로 생성한 경우
```python
# 데이터타입은 object(string이지만 pd에서는 object라고 표현)
s = pd.Series(['부장', '차장', '대리', '사원', '인턴'])
s

0    부장
1    차장
2    대리
3    사원
4    인턴
dtype: object
```


### - 다양한 타입(type)의 데이터를 섞은 경우
- Series에 다양한 데이터 타입의 데이터로 생성시, **object 타입**으로 생성됩니다.
```python
# 다른 곳에서 제공하는 엄청나게 많은 데이터를 판다스로 다루게 될텐데,
# 숫자와 글자가 다양하게 섞여있는 경우에는 오브젝트로 표시가 된다.
s = pd.Series([91, 2.5, '스포츠', 4, 5.16])
s

0      91
1     2.5
2     스포츠
3       4
4    5.16
dtype: object
```
### 1-2. 인덱싱 (indexing)
```python
s = pd.Series(['부장', '차장', '대리', '사원', '인턴'])
s

0    부장
1    차장
2    대리
3    사원
4    인턴
dtype: object
```
> Series 생성시 0부터 순차적으로 부여되는 index를 확인할 수 있습니다.
이를 RangeIndex라 부릅니다.
```python
s.index

RangeIndex(start=0, stop=5, step=1)

# RangeIndex는 start=0 ~ stop=5 까지의 범위를 가지므로 음수(negative) 색인이 불가하다.
s[-1]

ValueError: -1 is not in range
```

### - fancy indexing
```python
s[[1, 3]]

1    차장
3    사원
dtype: object
```


### - boolean indexing
- boolean index은 index list 에서 **True**인 **index 만 선택**합니다.

- 주의해야할 점은 반드시 boolean index list의 갯수와 Series의 갯수가 맞아야 합니다.

```python
# 모든 데이터를 처리할때 사용
# True에 해당하는 순서에 있는 데이터만 출력
s[[True, True, False, False, True]]

a    손흥민
b    김연아
e    김연경
dtype: object

# 조건을 걸어서 boolean index list를 먼저 만들어 준 뒤 대입 가능.
s = pd.Series([29, 99, np.nan, 11, 56], index=['a', 'b', 'c', 'd', 'e'])
s

s[s > 50]

b    99.0
e    56.0
dtype: float64
```

### 1-3. 속성(attribute)

### - values(값)

- values는 Series 데이터 값(value)만 numpy array 형식으로 가져 옵니다.
```python
s.values

array(['마케팅', '경영', '개발', '기획', '인사'], dtype=object)
```
### - ndim(차원)
- Series는 1차원 자료구조이기 때문에 ndim 출력시 1이 출력됩니다.
```python
s.ndim

1
```
### - shape(형상)
- shape은 데이터의 모양(shape)을 알아보기 위하여 사용하는데, Series의 shape은 **데이터의 갯수**를 나타냅니다.

- **튜플(tuple)** 형식으로 출력됩니다.
```python
s.shape

(5,)
```
### - NaN (Not a Number)

- Pandas에서 **NaN** 값은 비어있는 **결측치 데이터**를 의미합니다.

- 임의로 비어있는 값을 대입하고자 할 때는 numpy의 nan (np.nan)을 입력합니다.
```python
s = pd.Series(['선화', '강호', np.nan, '소정', '우영'])
s

0     선화
1     강호
2    NaN
3     소정
4     우영
dtype: object
```
### - 결측치 (NaN) 값 처리
- `isnull()`과 `isna()`은 NaN 값을 찾는 함수 입니다.

- `isnull()`과 `isna()`는 결과가 동일합니다.

```python
# NaN값을 찾는 함수
s.isnull()

a    False
b    False
c     True
d    False
e    False
dtype: bool
```
> notnull()은 NaN값이 아닌, 즉 비어있지 않은 데이터를 찾는 함수 입니다.
```python
# NaN값이 아닌 데이터만 찾는것
s.notnull()

a     True
b     True
c    False
d     True
e     True
dtype: bool
```
### - 슬라이싱
- (주의) 숫자형 index로 접근할 때는 **뒷 index가 포함되지 않습니다**.
```python
s[1:3]
```




<br/>
<br/>

## 2. 데이터프레임(DataFrame)

앞서, 판다스의 대표적인 두 가지 자료구조인 Series와 DataFrame 가운데 Series에 대해 배웠으므로, 이번에는 DataFrame에 대해 알아보도록 합니다.

`pd.DataFrame`
- 2차원 데이터 구조 (Excel 데이터 시트를 생각하시면 됩니다)
- 행(row), 열(column)으로 구성되어 있습니다.
- 각 열(column)은 각각의 데이터 타입 (dtype)을 가집니다.

### 2-1. 생성
- list 를 통한 생성할 수 있습니다. DataFrame을 만들 때는 **2차원 list를 대입**합니다.
- **columns를 지정**하면, DataFrame의 각 열에 대한 컬럼명이 붙습니다.

```python
pd.DataFrame([[1, 2, 3], 
              [4, 5, 6], 
              [7, 8, 9]], columns=['가', '나', '다'])

	가	나	다
0	1	2	3
1	4	5	6
2	7	8	9
```
- dictionary를 통한 생성도 가능합니다. dictionary의 key 값이 자동으로 column 명으로 지정됩니다.
```python
data = {
    'name': ['Kim', 'Lee', 'Park'], 
    'age': [24, 27, 34], 
    'children': [2, 1, 3]
}

pd.DataFrame(data)


    name age children
0	Kim	 24	  2
1	Lee	 27	  1
2	Park 34	  3
```

### 2-2. 속성

DataFrame은 다음의 속성을 가집니다.

    - index: index (기본 값으로 RangeIndex)
    - columns: column 명
    - values: numpy array형식의 데이터 값
    - dtypes: column 별 데이터 타입
    - T: DataFrame을 전치(Transpose)

### - index 지정
### - column 다루기
- DataFrame에 key 값으로 column의 이름을 지정하여 column을 선택할 수 있습니다.

- 1개의 column을 가져올 수 있으며, 1개의 column 선택시 Series가 됩니다.
```python
df

    name age children
a	Kim	 24	  2
b	Lee	 27	  1
c	Park 34	  3

df['name']

a     Kim
b     Lee
c    Park
Name: name, dtype: object

type(df['name'])

pandas.core.series.Series
# 타입을 보면 시리즈 타입인것을 알수있는데 df라는 데이터프레임은 시리즈들이 여러개 합쳐져있다.
# 그중에서 하나의 데이터만 가져오면 시리즈라는것을 알수 있다.
```
- 2개 이상의 column 선택은 **fancy indexing**으로 가능합니다.
```python
df[['name', 'children']]
```
- rename으로 column명 변경 가능합니다.
- DataFrame.rename(columns={'바꾸고자 하는 컬럼명': '바꿀 컬럼명'})
```python
df.rename({'name': '이름'}, axis=1)
df = df.rename( {'a' : 'z'}, axis=0 )
df


    name age children
z	Kim	  24    2
b	Lee	  27	1
c	Park  34	3

# inplace=True 옵션으로 변경사항을 바로 적용할 수 있으며, inplace를 입력하지 않으면 원본데이터를 바꾸지 않음.
# 결과를 변수에 재할당하게되면 원본데이터를 바꿈.

df.rename(columns={'name': '이름'}, inplace=True)
df

    이름  age children
z	Kim	  24    2
b	Lee	  27	1
c	Park  34	3
```