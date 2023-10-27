# 통계
- 통계는 데이터 분석에서 굉장히 중요한 요소입니다.
- 데이터에 대한 통계 계산식을 Pandas 함수로 제공하기 때문에 어렵지 않게 통계 값을 산출할 수 있습니다.

## describe() - 요약통계
- 전반적인 주요 통계를 확인할 수 있습니다.
- 기본 값으로 수치형(Numerical) 컬럼에 대한 통계표를 보여줍니다.
    - count: 데이터 개수
    - mean: 평균
    - std: 표준편차
    - min: 최솟값
    - max: 최대값
```python
df.describe()
```
![요약통계](/Pandas/assets/요약통계.png)

- 문자열 컬럼에 대한 통계표도 확인할 수 있습니다.

    - count: 데이터 개수
    - unique: 고유 데이터의 값 개수
    - top: 가장 많이 출현한 데이터 개수
    - freq: 가장 많이 출현한 데이터의 빈도수
```python
df.describe(include='object')
```
![문자열통계](/Pandas/assets/문자열통계.png)

</br>

## count() - 개수
- DataFrame 전체의 개수를 구하는 경우
```python
df.count()
```
- 단일 column의 데이터 개수를 구하는 경우
```python
df['age'].count()
```
</br>

## mean() - 평균
- 데이터의 평균
```python
df.mean(numeric_only=True)
# 글자 데이터가 섞여있을 경우 numeric_only=True를 적어줘야됌

survived       0.383838
pclass         2.308642
age           29.699118
sibsp          0.523008
parch          0.381594
fare          32.204208
adult_male     0.602694
alone          0.602694
dtype: float64
```
- age 컬럼에 대한 평균
```python
df['age'].mean()

29.69911764705882
```

</br>

### skipna=True 옵션
- skipna=False로 설정하게 된다면, NaN 값이 있는 column은 NaN 값으로 출력 됩니다.
```python
# skipna=False를 지정한 경우
df.mean(skipna=False, numeric_only=True)

survived       0.383838
pclass         2.308642
age                 NaN
sibsp          0.523008
parch          0.381594
fare          32.204208
adult_male     0.602694
alone          0.602694
dtype: float64

# skipna=True를 지정한 경우
df.mean(skipna=True, numeric_only=True)

survived       0.383838
pclass         2.308642
age           29.699118
sibsp          0.523008
parch          0.381594
fare          32.204208
adult_male     0.602694
alone          0.602694
dtype: float64
```
## median() - 중앙값
- 데이터의 중앙 값을 출력 합니다. 데이터를 오름차순 정렬하여 중앙에 위치한 값입니다.

- 이상치(outlier)가 존재하는 경우, mean()보다 median()을 대표값으로 더 선호합니다.

```python
# 나이의 평균(mean)과 중앙값(median)은 약간의 차이가 있음을 확인할 수 있습니다.
print(f"나이 평균: {df['age'].mean():.5f}\n나이 중앙값: {df['age'].median()}\n차이: {df['age'].mean() - df['age'].median():.5f}")

나이 평균: 29.69912
나이 중앙값: 28.0
차이: 1.69912
```
</br>

## sum() - 합계
- 데이터의 합계입니다. 문자열 column은 모든 데이터가 붙어서 출력될 수 있습니다.
```python
df.sum(numeric_only=True)
survived        342.0000
pclass         2057.0000
age           21205.1700
sibsp           466.0000
parch           340.0000
fare          28693.9493
adult_male      537.0000
alone           537.0000
dtype: float64
```
- 단일 column에 대한 합계 출력
```python
df['fare'].sum()

28693.9493
```
</br>

## cumsum() - 누적합, cumprod() - 누적곱
- cumsum(): 누적되는 합계를 구할 수 있습니다.
- cumprod(): 누적되는 곱도 구할 수 있으나, 일반적으로 값이 너무 커지므로 잘 활용하지는 않습니다.

</br>

## var() - 분산

</br>

## std() - 표준편차

</br>

## min() - 최소값, max() - 최대값
- min(): 최솟값
- max(): 최대값

</br>

## agg - aggregation: 통합 통계 적용 (복수의 통계 함수 적용)
- 단일 컬럼에 agg 적용
```python
df['age'].agg(['min', 'max', 'count', 'mean'])

min        0.420000
max       80.000000
count    714.000000
mean      29.699118
Name: age, dtype: float64
```
- 복수의 컬럼에 agg적용
```python
df[['age', 'fare']].agg(['min', 'max', 'count', 'mean'])

	    age	        fare
min	    0.420000	0.000000
max	    80.000000	512.329200
count	714.000000	891.000000
mean	29.699118	32.204208
```

## quantile() - 분위
- **Quantile이란 주어진 데이터를 동등한 크기로 분할하는 지점**을 말합니다
- 10%의 경우 0.1을, 80%의 경우 0.8을 대입하여 값을 구합니다.
```python
# 10% quantile
df['age'].quantile(0.1)

# 80% quantile
df['age'].quantile(0.8)
```

## mode() - 최빈값
- 최빈값은 가장 많이 출현한 데이터를 의미합니다.
```python
df['who'].mode()

0    man
Name: who, dtype: object

# 카테고리형 데이터에도 적용 가능합니다.
df['deck'].mode()

0    C
Name: deck, dtype: category
Categories (7, object): ['A', 'B', 'C', 'D', 'E', 'F', 'G']
```
## corr() - 상관관계
- corr()로 컬럼(column)별 **상관관계**를 확인할 수 있습니다.
- **-1~1 사이의 범위**를 가집니다.
- **-1에 가까울 수록 반비례** 관계, **1에 가까울수록 정비례 관계**를 의미합니다.
```python
df.corr(numeric_only=True)
# ex) survived가 커지면 커질 수록 adult_male이 작아진다.
# adult_male 수치가 높아질 수록 survived 확률은 줄어든다. -> 성인남성 생존확률은 떨어진다.

# fare이 높을수록 pclass 등급이 낮아지는걸 볼 수 있음 -> 가격이높을수록 1등급티켓이다.
```
![상관관계](/Pandas/assets/상관관계.png)
