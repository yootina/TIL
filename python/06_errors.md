# 1. Error(오류)

## 1.1 syntax error(구문 오류) - 실행 전 오류
- 괄호의 개수, 들여쓰기의 문제 등 문법적으로 오류 발생

```python
if True:
    pass
else

 Cell In[1], line 3
    else
        ^
SyntaxError: expected ':'
```
<br/>

```python
print('hi'

 Cell In[2], line 1
    print('hi'
              ^
SyntaxError: incomplete input
```
<br/>

```python
if True print('hello')

Cell In[3], line 1
    if True print('hello')
            ^
SyntaxError: invalid syntax
```
<br/>

### 1.1.1 exception(예외) - 실행 후 오류
- 코드 실행하는 중에 발생하는 에러를 뜻함.

#### - ZeroDivisionError: 0으로 나누려는 경우에 발생하는 에러

```python
print(5/0)

ZeroDivisionError                         Traceback (most recent call last)
Cell In[4], line 1
----> 1 print(5/0)

ZeroDivisionError: division by zero
```
<br/>

#### - NameError: 지역변수, 전역 변수 이름을 찾을 수 없는 경우에 NameError 가 발생

```python
print(hello)

NameError                                 Traceback (most recent call last)
Cell In[5], line 1
----> 1 print(hello)

NameError: name 'hello' is not defined
```
<br/>

#### - TypeError: 잘못된 타입을 전달했을 때 발생하는 에러

```python
1 + '1'

TypeError                                 Traceback (most recent call last)
Cell In[6], line 1
----> 1 1 + '1'

TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

```python
'1' + 1

TypeError                                 Traceback (most recent call last)
Cell In[7], line 1
----> 1 '1' + 1

TypeError: can only concatenate str (not "int") to str
```

```python
# random.sample(sequence, k) 처럼 k자리에 반환될 리스트의 갯수를 입력해야됌

import random
random.sample([1, 2, 3, 4])

TypeError                                 Traceback (most recent call last)
Cell In[11], line 1
----> 1 random.sample([1, 2, 3, 4])

TypeError: Random.sample() missing 1 required positional argument: 'k'
```

```python
# random.sample(sequence, k) => k 자리에 너무 많은 갯수를 입력했을 때
random.sample([1, 2, 3, 4], 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2)

TypeError                                 Traceback (most recent call last)
Cell In[12], line 1
----> 1 random.sample([1, 2, 3, 4], 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2)

TypeError: Random.sample() takes 3 positional arguments but 14 were given
```
<br/>

#### - ValueError: 부적절한 값을 인자로 받았을 때 발생하는 에러

```python
int('4.5')

ValueError                                Traceback (most recent call last)
Cell In[13], line 1
----> 1 int('4.5')

ValueError: invalid literal for int() with base 10: '4.5'
```

```python
numbers = [1, 2, 3, 4]
numbers.index(100)

ValueError                                Traceback (most recent call last)
Cell In[14], line 2
      1 numbers = [1, 2, 3, 4]
----> 2 numbers.index(100)

ValueError: 100 is not in list
```
<br/>

#### - IndexError: 인덱스 범위를 벗어나는 경우에 발생하는 에러

```python
numbers = [1, 2, 3, 4]
numbers[100]

IndexError                                Traceback (most recent call last)
Cell In[16], line 2
      1 numbers = [1, 2, 3, 4]
----> 2 numbers[100]

IndexError: list index out of range
```
<br/>

#### - KeyError: 딕셔너리에서 접근하려는 키 값이 없을 때 발생하는 에러

```python
my_dict = {
    'apple': '사과',
    'banana': '바나나',
}
my_dict['melon']

KeyError                                  Traceback (most recent call last)
Cell In[18], line 5
      1 my_dict = {
      2     'apple': '사과',
      3     'banana': '바나나',
      4 }
----> 5 my_dict['melon']

KeyError: 'melon'
```
<br/>

#### - 기타에러

```python
# 모듈을 찾을 수 없다는 에러
import asdf

ModuleNotFoundError                       Traceback (most recent call last)
Cell In[20], line 1
----> 1 import asdf

ModuleNotFoundError: No module named 'asdf'
```

```python
# 무한반복루프 키보드 중지
while True:
    continue

KeyboardInterrupt                         Traceback (most recent call last)
Cell In[21], line 2
      1 while True:
----> 2     continue

KeyboardInterrupt: 
```

## 1.2 예외처리(예외를 해결하는 것)

- `try, except` 예외처리
```python
try:
    실행할 코드
except 예외:
    예외가 발생했을 때 처리하는 코드
```

```python
# except 뒤에 발생할 에러를 직접 넣고 처리 가능.
try:
    num = int(input('숫자를 입력해주세요 : '))
    print(f'{num}의 세제곱은 {num ** 3}입니다.')
except ValueError:
    print('숫자를 입력하세요!!!!!')
```

```python
# except 뒤에 여러가지 에러를 넣고 처리 가능.
try:
    num = int(input('100을 나눌 값을 입력해주세요 : '))
    print(f'100을 {num}으로 나누면 {100/num}입니다.')
except ValueError:
    print('입력한 정보는 숫자가 아닙니다')
except ZeroDivisionError:
    print('수학적으로 0으로는 나눌 수 없습니다.')
```

```python
# except 뒤에 에러를 넣지 않고도 처리 가능.
try:
    num = int(input('100을 나눌 값을 입력해주세요 : '))
    print(f'100을 {num}으로 나누면 {100/num}입니다.')
except:
    print('무엇인가 잘못되었습니다.')
```

```python
# 발생할 에러를 직접 넣고, 아래에 직접 호출하지않아도 가능
try:
    print(asdf)
    num = int(input('100을 나눌 값을 입력해주세요 : '))
    print(f'100을 {num}으로 나누면 {100/num}입니다.')
except (ValueError, ZeroDivisionError):
    print('무엇인가 잘못되었습니다.')
except:
    print('wrong')
```
<br/>

- 예외의 에러 메시지 받아오기
    - except에서 as 뒤에 변수를 지정하면 발생한 예외의 에러 메시지를 받아올 수 있음

```python
try:
    실행할 코드
except 예외 as 변수:
    예외가 발생했을 때 처리하는 코드
```

```python
try:
    my_list = [1, 2, 3]
    print(my_list[100])
except IndexError as err:
    print('범위에 문제가 있습니다')
    print(err)

범위에 문제가 있습니다
list index out of range
```
<br/>

- `else, finally` 사용

```python
# else => 예외가 발생하지 않았을 때 실행하는 코드

try:
    numbers = [1, 2, 3]
    num = numbers[100]
except:
    print('오류발생')
else:
    print(num ** 3)
```


```python
# finally => 예외 상황과 무관하게 무조건 최종적으로 실행되는 코드
try:
    numbers = [1, 2, 3]
    num = numbers[1]
except:
    print('오류발생')
finally:
    print('end')
```
<br/>

- `raise`: 예외 발생시키기

```python
for i in range(100):
    if i == 50:
        print(i)
        raise

RuntimeError                              Traceback (most recent call last)
Cell In[51], line 4
      2 if i == 50:
      3     print(i)
----> 4     raise

RuntimeError: No active exception to reraise
```

```python
# 연습
def my_div(num1, num2):
    try:
        result = num1 / num2
    except ZeroDivisionError:
        print('0으로 나눌수 없습니다.')
        # return None
    except:
        print('숫자를 넣어야 합니다.')
        # return None
    else:
        return result



print(my_div(5, 0))
print(my_div('5', '0'))
print(my_div(5, 2))

0으로 나눌수 없습니다.
None
숫자를 넣어야 합니다.
None
2.5
```