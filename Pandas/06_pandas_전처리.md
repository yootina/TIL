# 전처리

### 새로운 컬럼 추가
- 임의의 값을 대입하여 새로운 컬럼을 추가할 수 있습니다.

### 삭제
- 삭제는 **행(row) 삭제**와 **열(column) 삭제**로 구분할 수 있습니다.
### 행 (row) 삭제
- 행 삭제시 index를 지정하여 삭제합니다.
### 열 (column) 삭제
- 열 삭제시 반드시 **axis=1** 옵션을 지정해야 합니다.
- 다수의 컬럼(column) 삭제도 가능합니다.
- 삭제된 내용을 바로 적용하려면 `inplace=True`를 지정합니다.

## 컬럼간 연산

```python
df1['family'] = df1['sibsp'] + df1['parch']
```
- 문자열의 합 (이어붙히기)도 가능하며, 컬럼간 연산시 round()를 사용하여 소수점 자릿수를 지정할 수 있습니다.
- round(숫자, 소수 몇 째자리)
```python
df1['round'] = round(df1['fare'] / df1['age'], 2)
```

## 타입 변환 (astype)
- int32로 변경
- float32로 변경
- object로 변경
- category로 변경. (category로 변경시에는 Categories가 같이 출력 됩니다.)

## pd.to_numeric() - 수치형 변환
- object나 numerical type이 아닌 컬럼을 **수치형(numerical) 컬럼으로 변환할 때 사용**합니다.

> 해당 컬럼이 숫자형컬럼으로 보이지만 object타입으로 지정되어있을 때 `pd.to_numeric()`으로 변환을 시도한다. </br>
> 숫자형으로 바꿀 때 NaN값이나 숫자로 변환이 불가능한 문자열이 존재할 때 변환에 실패하게 된다. </br>
> errors= 옵션 값을 바꾸어 해결할 수 있으며, `errors='coerce'`로 지정하면 잘못된 문자열은 NaN 값으로 치환하여 변환한다.

## pd.cut() - 구간 나누기(binning)
- 연속된 수치(continuous values)를 구간으로 나누어 카테고리화 할 때 사용합니다.

## pd.qcut() - 동일한 개수를 갖도록 구간 분할
- pd.cut()과 유사하지만, quantity 즉 데이터의 분포를 최대한 비슷하게 유지하는 구간을 분할 합니다.