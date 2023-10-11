# 1. 모듈
- 모듈(module)은 각종 변수, 함수, 클래스를 담고 있는 파일(미리 만들어놓은 파일)
- 모듈은 재사용을 편하게 하기 위해서, 비슷한 동작을 하는 것끼리 모아놓기 위해서 사용


## 1.1 import로 모듈 가져오기
- 모듈은 `import` 키워드로 가져올 수 있음.

```python
# 모듈의 함수는 아래와 같이 모듈.함수() 형식으로 사용
import fibo

fibo.fib_loop(10)
```
> - 에러
> 1. AttributeError: module ... has no attribute ... : 모듈의 변수나 함수의 이름을 잘못되었을 때 발생하는 에러 <br/>
> 2. ModuleNotFoundError: No module named ... : 모듈의 이름이 잘못되었을 때 발생하는 에러
>  <br/>

# 2. 패키지
- 특정 기능과 관련된 여러 모듈을 묶은 것
- **패키지 안에 `__init__.py` 파일이 있어야 패키지로 인식** 

```python
myPackage/
    __init__.py
    math/
        __init__.py
        fibo.py
        fomula.py
```

## 2.1 from import로 패키지의 모듈에서 일부만 가져오기
- from import를 사용하여 모듈에서 변수, 함수, 클래스를 가져올 수 있음
```python
# MyPackage 라는 폴더에서 math 폴더에 들어간 후 fomula 파일 가져오기
from myPackage.math import fomula

# fomula 파일에서 가져온 함수실행하기
fomula.pi

# 모든 변수, 함수, 클래스를 가져오는 방법
from myPackage.math.fibo import *

# from '패키지,모듈' import '변수' as '이름'으로 이름이 충돌날 때 다른식으로 이름 변경 가능
fomula = 1234
from myPackage.math import fomula as f

print(fomula)
print(f)
```
## 2.2 파이썬 내장 패키지

### 2.2.1 math

```python
import math

# 원주율
>>> math.pi

# 자연 상수
>>> math.e

# 올림 함수, 소수점을 올림 하여 정수로 만든다
>>> math.ceil()

# 내림 함수, 소수점을 내려 정수로 만든다
>>> math.floor()

# 제곱근의 값을 반환
>>> math.sqrt()

# 팩토리얼 함수, 팩토리얼은 1부터 인자로 주어진 값까지 모두 곱하는 값을 반환
>>> math.factorial()
```

### 2.2.2 random

```python
import random

# random모듈의 random() 함수, 0이상 1미만의 숫자중에서 랜덤 추출
>>> random.random()
0.90389642027948769

# seed 함수, '무작위'의 결과를 특정한 값으로 고정
>>> random.seed()

random.random()
0.9560342718892494

# 시퀀스를 뒤죽박죽 섞는 함수
>>> random.shuffle()

a = [1, 2, 3, 4, 5]
print(a)

random.shuffle(a)
print(a)

[1, 2, 3, 4, 5]
[1, 4, 2, 3, 5]

# 무작위로 하나의 원소를 추출
>>> random.choice()

rcp = ['가위', '바위', '보']
random.choice(rcp)
'보'

# 무작위로 하나의 정수를 추출
>>> random.randint()

random.randint(1, 10)
10

# 무작위로 여러개의 원소를 추출 (중복추출 X)
>>> random.sample()

random.sample(range(1, 46), 6)
[7, 4, 37, 42, 44, 18]
```

### 2.2.3 datetime

- 날짜와 시간을 다루기 위한 패키지
- datetime 아래와 같이 가져오기

```python
from datetime import datetime
```

```python
# 현재 날짜와 시간 출력
>>> datetime.now()

datetime.datetime(2023, 10, 11, 10, 21, 25, 815868)

#현재 날짜 출력
>>> datetime.today()

today = datetime.today()
print(today)

2023-10-11 10:22:18.511367

# D-day 계산
>>> datetime.timedelta()

future = timedelta(days=3)
print(future)

# 날짜와 시간(datetime)을 문자열로 출력
>>> datetime.strftime()

now = datetime.now()
now.strftime('%Y년 %m월 %d일 %a')
'2023년 10월 11일 Wed'

# => 0~6 / 월~일로 나타냄
>>> now.weekday()

2
```

