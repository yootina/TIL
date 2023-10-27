# concat(), merge

## concat() - 데이터 연결
- `concat()`은 DataFrame을 연결합니다. 단순하게 지정한 DataFrame을 이어서 연결합니다.

### 행 방향으로 연결
```python
pd.concat([gas1, gas2])
```
![concat1](/Pandas/assets/concat1.png)

- 연결 하면서 index를 무시하고 연결 할 수 있습니다.
```python
gas = pd.concat([gas1, gas2], ignore_index=True)
gas
```
![concat2](/Pandas/assets/concat2.png)


### 열 방향으로 연결
- 열(column) 방향으로 연결 가능하며, **axis=1**로 지정합니다.
- 같은 index 행끼리 연결됩니다.

</br></br>

## merge() - 병합
- 서로 **다른 구성의 DataFrame**이지만, **공통된 key값(컬럼)을 가지고 있다면 병합**할 수 있습니다.
</br>

[df1]
![merge1](/Pandas/assets/merge1.png)

</br>

[df2]
![merge2](/Pandas/assets/merge2.png)

</br>

```python
pd.merge(df1, df2)
```
![merge3](/Pandas/assets/merge3.png)