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

### - numpy array로 생성한 경우
### - dtype을 지정한 경우
### - list로 생성한 경우
### - 다양한 타입(type)의 데이터를 섞은 경우

### 1-2. 인덱싱 (indexing)
### - fancy indexing
### - boolean indexing

### 1-3. 속성(attribute)
### - values(값)
### - ndim(차원)
### - shape(형상)

### - NaN (Not a Number)
### - 결측치 (NaN) 값 처리

### - 슬라이싱


<br/>
<br/>

## 2. 데이터프레임(DataFrame)

앞서, 판다스의 대표적인 두 가지 자료구조인 Series와 DataFrame 가운데 Series에 대해 배웠으므로, 이번에는 DataFrame에 대해 알아보도록 합니다.

`pd.DataFrame`
- 2차원 데이터 구조 (Excel 데이터 시트를 생각하시면 됩니다)
- 행(row), 열(column)으로 구성되어 있습니다.
- 각 열(column)은 각각의 데이터 타입 (dtype)을 가집니다.

### 2-1. 생성
### 2-2. 속성

### - index 지정
### - column 다루기
