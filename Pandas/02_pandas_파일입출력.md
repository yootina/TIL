# 파일 입출력
- 데이터 분석에서 일반적으로 사용되는 파일 형식인 엑셀(Excel)과 CSV (Comma Separated Value)을 로드하고 데이터프레임(DataFrame)을 엑셀(Excel)이나 CSV형식으로 저장하는 방법에 대해 학습한다.


### 모듈 import
```python
from IPython.display import Image
import numpy as np
import pandas as pd
```

## Excel

### Excel - 불러오기
### Excel - 저장하기
### Excel - 여러개의 시트에 저장

## CSV (Comma Separated Values)
- 한 줄이 한 개의 행에 해당하며, 열 사이에는 쉼표(,)를 넣어 구분합니다.
- Excel보다는 훨씬 가볍고 차지하는 용량이 적기 때문에 대부분의 파일데이터는 csv 형태로 제공됩니다.

(참고) 쉼표를 찍어 놓은 금액 데이터(100,000)를 CSV에 직접 집어넣으면 나중에 해석할 때 서로 다른 열로 취급되므로 문제가 될 수 있습니다. 해결책으로 쉼표 대신 탭 문자(\t)를 구분자로 사용하는 것이다. 이러한 경우 Tab Separated Values(TSV)라고 부른다.

### CSV - 불러오기
### CSV - 큰 파일 데이터 끊어서 불러오기
### CSV - 저장하기
