# groupby, pivot-table

## apply - 함수를 적용
- apply()는 데이터 전처리시 굉장히 많이 활용하는 기능입니다. 좀 더 복잡한 logic을 컬럼 혹은 DataFrame에 적용하고자 할 때 사용합니다.

### 함수(function) 정의

```python
def transform_who(x):
    if x == 'man':
        return '남자'
    elif x == 'woman':
        return '여자'
    else:
        return '아이'

df['who'].apply(transform_who)

0      남자
1      여자
2      여자
3      여자
4      남자
       ..
886    남자
887    여자
888    여자
889    남자
890    남자
Name: who, Length: 891, dtype: object

# 분포를 확인하면 다음과 같다.
df['who'].apply(transform_who).value_counts()

who
남자    537
여자    271
아이     83
Name: count, dtype: int64
```

## apply() - lambda 함수
- 간단한 logic은 함수를 굳이 정의하지 않고, lambda 함수로 쉽게 해결할 수 있습니다.

## groupby() - 그룹
- 데이터를 특정 기준으로 그룹핑할 때 활용합니다. 엑셀의 피봇테이블과 유사합니다.

- 2개 이상의 컬럼으로 그룹 가능
- 1개의 특정 컬럼에 대한 결과 도출 가능

## reset_index(): 인덱스 초기화
- `reset_index()`: 그룹핑된 데이터프레임의 index를 초기화하여 새로운 데이터프레임을 생성합니다.
```python
# index 초기화
df.groupby(['sex', 'pclass'])['survived'].mean(numeric_only=True).reset_index()
```

## 다중 통계 함수 적용
- 여러 가지의 통계 값을 적용할 때는 `agg()`를 사용합니다.
```python
# 성별, 좌석등급 별 통계
df.groupby(['sex', 'pclass'])[['survived', 'age']].agg(['mean', 'sum', 'max', 'median'])
```
![agg](/Pandas/assets/agg.png)

## pivot_table()
- 피벗테이블은 엑셀의 피벗과 동작이 유사하며, groupby()와도 동작이 유사합니다.
- 기본 동작 원리는 `index`, `columns`, `values`를 지정하여 피벗합니다.
```python
# 1개 그룹에 대한 단일 컬럼 결과
# index에 그룹을 표기
df.pivot_table(index='who', values='survived')

# columns에 그룹을 표기
df.pivot_table(columns='who', values='survived')

# 다중 그룹에 대한 단일 컬럼 결과
df.pivot_table(index=['who', 'pclass'], values='survived')

# index에 컬럼을 중첩하지 않고 행과 열로 펼친 결과
df.pivot_table(index='who', columns='pclass', values='survived')

# 다중 통계함수 적용
df.pivot_table(index='who', columns='pclass', values='survived', aggfunc=['sum', 'mean'])
```