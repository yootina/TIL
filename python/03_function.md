# 1. 함수(Function)

- 어떤 기능을 하도록 만든 코드의 묶음.
- 정의된 함수는 필요한 순간 호출해서 재사용이 가능함.


## 1.1 함수의 선언과 호출

```python
- 함수의 선언(만들다)
def func_name(parameter1, parameter2):
    code1
    code2
    ...
    return value

- 함수의 호출(실행)
func_name(parameter1, parameter2)
```

```python
# rectangle() 함수 만들기

def rectangle(height, width):
    area = height * width
    perimeter = (height + width) * 2
    print(area, perimeter)
rectangle(100, 50)
rectangle(10, 20)

5000 300
200 60

# my_max() 함수 만들기

def my_max(num1, num2):
    if num1 > num2:
        print(num1)
    elif num1 < num2:
        print(num2)
    else:
        print('같습니다')

my_max(1, 2)
my_max(5, 5)

2
'같습니다'
```
- 내장함수 목록 확인
```python
dir(__builtins__)
```

## 1.2 함수의 return
- 함수가 return을 만나면 해당 값을 반환하고 함수를 종료.
- 만약 return이 없다면 None을 자동으로 반환
- return은 오직 하나의 객체만 반환.

```python

# 각각의 정수를 받아 큰 값을 출력
def my_max2(num1, num2):
    if num1 > num2:
        return num1
    elif num1 < num2:
        return num2
    else:
        return 'same'
        
a = my_max2(2, 3)
print(a)

3

# 리스트 두개를 받아서 각각 더한 결과를 비교하여 값이 큰 리스트를 반환하기

def my_list_max(a, b):
    if sum(a) > sum(b):
        return a
    else:
        return b

x = my_list_max([1, 3, 4], [2, 4, 5])
print(x)

[2, 4, 5]
```

## 1.3 함수의 인자/인수

### 1.3.1 위치인수
- 기본적으로 함수는 인수의 위치로 판단합니다.
```python
def cylinder(r, h):
    return 3.14 * r**2 * h

print(cylinder(10, 5))
print(cylinder(5, 10))

1570.0
785.0
```

### 1.3.2 기본값
- 함수가 호출될 때 인자를 지정하지 않아도 기본값을 설정할 수 있다.
```python
def func(p1=v1):
    code...
    return p1
```
```python
def greeting(name='익명'):
    return f'{name}님 안녕하세요!!'
greeting('이름')

'이름님 안녕하세요!!'
greeting()

'익명님 안녕하세요!!'
```

### 1.3.3 키워드 인자
- 함수를 호출할 때 내가 원하는 위치에 직접적으로 특정인자를 전달 가능.
```python
def greeting(age, name='익명'):
    return f'{name}님 은 {age}살입니다.'

print(greeting(10))
print(greeting(20, '홍길동'))
# 순서가 달라도 필수적인 요소를 지정해주면 사용가능
print(greeting(name='홍길동', age=30))

익명님 은 10살입니다.
홍길동님 은 20살입니다.
홍길동님 은 30살입니다.
```

### 1.3.4 가변인자 리스트

- 정해지지 않은 임의의 숫자를 받기 위해서는 가변인자를 활용.
- 가변인자는 tuple형태로 처리가 되며, `*`로 표현한다.

```python
def func(*args):
    code
    ...
```
```python
# args(argument의 약자)가 tuple임을 확인.
def my_func(*args):
    print(type(args))
    print(args)
my_func(1, 2, 3, 4, 5, 6)

<class 'tuple'>
(1, 2, 3, 4, 5, 6)
```

```python
def my_print(*words):
    print(words)
    print(type(words))

print('a', 'b', 'c', 'd', '공간')
print('a', 'b', 'c', 'd', sep='/')
# 앞에 있는 오브젝트는 가변인자 이기 때문에 구분선을 넣고싶으면 항상 키워드 인자로 넣기

a b c d 공간
a/b/c/d
```

```python
# 정수 여러개 받아서 가장 큰 값을 반환
def my_max(*numbers):
    result = numbers[0]
    
    for number in numbers:
        if result < number:
            result = number

    return result
print(my_max(1, 6, 3, 4, 5))
6
```

### 1.3.5 정의되지 않은 키워드 인자 처리하기

- 키워드 매개변수를 사용할 때는 매개변수 앞에 별 `2개(**)`를 붙인다.
- 매개변수 이름 앞에 `**`을 붙이면 매개변수는 딕셔너리가 되고 모든 Key=Value 형태의 입력값이 그 딕셔너리에 저장된다.

```python
# kwargs = ‘keyword arguments’의 약자
def func(**kwargs):
    code
    ...
```
```python
def fake_dict(**kwargs):
    for key, value in kwargs.items():
        print(f'{key}는 {value}입니다.')

fake_dict(a=10, b=20)
fake_dict(korean='안녕', english='hello')

a는 10입니다.
b는 20입니다.
korean는 안녕입니다.
english는 hello입니다.
```

### 1.3.6 dictionary를 인자로 넣기(unpacking)
```python
def sign_up(id, pw, pw_confirmation):
    if pw == pw_confirmation:
        print(f'{id}님 회원가입이 완료되었습니다.')
    else:
        print('비밀번호가 일치하지 않습니다.')

sign_up('change', '1234', '1234')
sign_up('change', '1234', '12345')

change님 회원가입이 완료되었습니다.
비밀번호가 일치하지 않습니다.
```