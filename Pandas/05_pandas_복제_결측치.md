# 복제, 결측치

### copy
- DataFrame을 복제합니다. 복제한 DataFrame을 수정해도 원본에는 영향을 미치지 않습니다.
- `copy()`로 DataFrame을 복제합니다

## 결측치
- 결측치는 비어있는 데이터를 뜻한다.
- 결측치에 대한 처리는 매우 중요하며, 다음의 내용을 알아야한다.
    1. 결측 데이터 확인
    2. 결측치가 아닌 데이터 확인
    3. 결측 데이터 채우기
    4. 결측 데이터 제거하기

### 결측치 확인 - isnull(), isnan()

- 컬럼(column)별 결측치의 갯수를 확인하기 위해서는 `sum() `함수를 붙혀주면 됩니다.

- `sum()`은 Pandas의 통계 관련 함수이며, 통계 관련 함수는 추후에 더 자세히 알아볼 예정입니다.

### isnull()
```python
df.isnull().sum()
```
### isna()
- isnull() 과 동작 같음.
```python
df.isna().sum()
```

## 결측치가 아닌 데이터 확인 - notnull()
- `notnull()`은 `isnull()` 정확히 반대 개념.
```
df.notnull().sum()

survived       891
pclass         891
sex            891
age            714
sibsp          891
parch          891
fare           891
embarked       889
class          891
who            891
adult_male     891
deck           203
embark_town    889
alive          891
alone          891
dtype: int64
```
## 결측 데이터 필터링
- isnull() 함수가 결측 데이터를 찾는 **boolean index** 입니다. 즉, loc에 적용하여 조건 필터링을 걸 수 있습니다.
```
df.loc[df['age'].isnull()]
```

## 결측치 채우기 - fillna()
- `fillna()`를 활용하면 결측치에 대하여 일괄적으로 값을 채울 수 있습니다.

```python
df1['deck'].fillna('A')

0      A
1      C
2      A
3      C
4      A
      ..
886    A
887    B
888    A
889    C
890    A
Name: deck, Length: 891, dtype: category
Categories (7, object): ['A', 'B', 'C', 'D', 'E', 'F', 'G']
```

</br>

- 하지만, 없는 카테고리로 채워주고자 할 때는 먼저 **add_categories**로 카테고리를 추가한 후 채워야 합니다.
```python
# add_categories (카테고리 추가)
# cat은 category의 지정자
df1['deck'].cat.add_categories('No Data').fillna('No Data')

0      No Data
1            C
2      No Data
3            C
4      No Data
        ...   
886    No Data
887          B
888    No Data
889          C
890    No Data
Name: deck, Length: 891, dtype: category
Categories (8, object): ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'No Data']
```

</br>

## 통계값으로 채우기

### 평균으로 채우기
```python
df1['age'].fillna(df1['age'].mean()).tail()
```
### 중앙값으로 채우기
```python
df1['age'].fillna(df1['age'].median()).tail()
```
### 최빈값으로 채우기
- 최빈값(mode)으로 채울 때에는 반드시 **0번째 index 지정**하여 값을 추출한 후 채워야 합니다.
```python
df1['deck'].mode()[0]

'C'

df1['deck'].fillna(df1['deck'].mode()[0]).tail()

886    C
887    B
888    C
889    C
890    C
Name: deck, dtype: category
Categories (7, object): ['A', 'B', 'C', 'D', 'E', 'F', 'G']
```

</br>

## NaN 값이 있는 데이터 제거하기 (dropna)
- `dropna()`로 1개 라도 NaN 값이 있는 행은 제거할 수 있습니다. `(how='any')`

- 기본 옵션 값은 how=any로 설정되어 있으며, 다음과 같이 변경할 수 있습니다.
    - any: 1개 라도 NaN값이 존재시 drop
    - all: 모두 NaN값이 존재시 drop