# 파일 입출력
- 데이터 분석에서 일반적으로 사용되는 파일 형식인 엑셀(Excel)과 CSV (Comma Separated Value)을 로드하고 데이터프레임(DataFrame)을 엑셀(Excel)이나 CSV형식으로 저장하는 방법에 대해 학습한다.


### 모듈 import
```python
from IPython.display import Image
import numpy as np
import pandas as pd
```
</br></br>

## Excel
### Excel - 불러오기
> Excel 데이터를 바로 읽어들일 수 있으며, sheet_name을 지정하면 해당 sheet를 가져옵니다.

### Excel - 저장하기
- DataFrame을 Excel로 저장할 수 있으며, Excel로 저장시 파일명을 지정합니다.

- **index=False** 옵션은 가급적 꼭 지정하는 옵션입니다. 지정을 안하면 index가 별도의 컬럼으로 저장되게 됩니다.
- sheet_name을 지정하여, 저장할 시트의 이름을 변경할 수 있습니다.

### Excel - 여러개의 시트에 저장
- 여러 개의 시트에 저장하기 위해서는 ExcelWriter를 사용해야 합니다.

</br></br>

## CSV (Comma Separated Values)
- 한 줄이 한 개의 행에 해당하며, 열 사이에는 쉼표(,)를 넣어 구분합니다.
- Excel보다는 훨씬 가볍고 차지하는 용량이 적기 때문에 대부분의 파일데이터는 csv 형태로 제공됩니다.

> (참고) 쉼표를 찍어 놓은 금액 데이터(100,000)를 CSV에 직접 집어넣으면 나중에 해석할 때 서로 다른 열로 취급되므로 문제가 될 수 있습니다. 해결책으로 쉼표 대신 탭 문자(\t)를 구분자로 사용하는 것이다. 이러한 경우 Tab Separated Values(TSV)라고 부른다.

### CSV - 불러오기
```python
df = pd.read_csv('파일이름.csv')
```
### CSV - 큰 파일 데이터 끊어서 불러오기
- 데이터의 크기가 매우 큰 경우 memory에 한 번에 로드할 수 없습니다.
- chunksize를 지정하고 chunksize만큼 끊어서 불어와서 처리하게 되면 용량이 매우 큰 데이터도 처리할 수 있습니다.
> 예시 : chunksize=10: 10개의 데이터를 로드합니다.
### CSV - 저장하기
- 저장하는 방법은 excel과 유사합니다. 다만, csv파일 형식에는 sheet_name 옵션은 없습니다.
