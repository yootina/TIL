# 1. 제어문

## 1.1. 조건문(if문)

-  `if` 문은 반드시 참/거짓을 판단 할 수 있는 `조건식`과 함께 사용한다.<br/>
    -  `조건식`이 `참`인 경우 `:(콜론)` 이후의 문장을 실행한다.<br/>
    -  `조건식`이 `거짓`인 경우 `else :` 이후의 문장을 실행한다.<br/>

```python
if <조건식>:
    if문의 조건식이 참인 경우 실행하는 코드
else:
    if문의 조건식이 거짓인 경우 실행하는 코드
```

```python
my_string = input()

if my_string == '12/25':
    print('크리스마스입니다.')
else:
    print('크리스마스가 아닙니다.')
```

```python
num = int(input('숫자를 입력해주세요 : '))
# input 함수는 문자형태이기 떄문에 int로 숫자형태로 바꿔주기

if num % 2 == 0:
    print('짝수입니다')
else:
    print('홀수입니다')
print(type(num))

숫자를 입력해주세요 :  10
짝수입니다
<class 'int'>
```

```python
# num을 2로 나눈 나머지는 0, 1 두가지 경우가 있다.
# if 조건식에 0, 1은 자동형변환이 일어나 False, True로 변환된다.

num = int(input('숫자를 입력해주세요 : '))

if num % 2:
    print('홀수입니다')
else:
    print('짝수입니다')
print(type(num))

숫자를 입력해주세요 :  13
홀수입니다
<class 'int'>
```

### 1.1.1 복수 조건문 (elif)

- 2개 이상의 조건문을 활용할 경우 `elif<조건식>:` 을 활용한다.

```python
if <조건식>:
    if문의 조건식이 참인 경우 실행하는 코드
elif <조건식>:
    elif 조건식이 참인 경우 실행하는 코드
...
else:
    위의 조건식에 하나도 부합하지 않는 경우 실행하는 코드
```

```python
# 2개 이상의 조건문을 활용할 경우 elif<조건식>:을 활용한다.

# 90점 이상 'A' (95이상이라면 good 추가)
# 80점 이상 'B'
# 70점 이상 'C'
# 그 외 'F'

score = int(input('성적을 입력하세요 : '))
# input 함수는 문자형태이기 떄문에 int로 숫자형태로 바꿔주기
if 90 <= score:
    print('A')
        if 95 <= score:
            print('good')
elif 80 <= score < 90:
    print('B')
elif 70 <= score < 80:
    print('C')
else:
    print('F')
```

### 1.1.2 조건부 표현식

```python
true_value if <조건식> else false_value
= 조건문이_참인_경우의_값 if <조건식> else 조건문이_거짓인_경우의_값
```

```python
num = 10
if num % 2 == 1:
    result = '홀수'
else:
    result = '짝수'
print(result)

짝수

# 위 조건식을 조건부 표현식으로 바꾼다면

result = '홀수' if num % 2 == 1 else '짝수'
print(result)
```

## 2. 반복문

### 2.1 while문
- while문은 조건식이 `참(True)`인 경우 `반복적으로` 코드를 실행.

```python
while <조건식>:
    실행할 코드
```

```python
a = 0
while a < 5:
    print(a)
    a += 1
    # a = a + 1

0
1
2
3
4
```
```python
greeting = ''
while greeting != '안녕':
    greeting = input('안녕이라고 해줘 : ')

안녕이라고 해줘 :  하이
안녕이라고 해줘 :  헬로우
안녕이라고 해줘 :  안녕
```
#### 2.1.1 while문 강제로 빠져나가기(break)
- while문은 조건문이 참인 조건하에 반복적으로 수행한다. while문을 수행하다가 특정 조건이 만족된 경우에 `break`를 사용한다.

```python
cosmetic = 10
people = 15

while people:
    print('화장품 당첨!')
    cosmetic -= 1
    print(f'남은 화장품은 {cosmetic}개 입니다')
    if cosmetic == 0:
        print('선착순 이벤트가 끝났습니다. 다음기회에')
        break
# 이 예시처럼 break는 while문을 수행하다가 특정 조건이 만족된 경우에 while문 자체를 빠져나오고 싶을 때 사용한다.
```

#### 2.1.2 while문의 처음으로 돌아가기(continue)
- while 반복문을 실행하다가 특정 조건을 만족할 때 continue이후의 코드들을 실행하지않고 위로 올라가 반복을 계속 수행한다.

```python
a = 0
while a < 10:
    a += 1
    if a % 2 == 0:
        continue
    print(a)

1
3
5
7
9
```

### 2.2 for문
- for문은 `정해진 범위 내(sequence)`에서 `순차적으로` 코드를 실행.

```python
for variable in sequence
    실행할 코드
```
```python
# for문 예제
numbers = [1, 2, 3, 4, 5]

for number in numbers:
    print(number)

1
2
3
4
5
```

#### 2.2.1 for문과 함께 사용하는 range함수

```python
# 1~30까지 숫자중에서 홀수를 출력

numbers = range(1,30)
# range함수는 1부터 30미만의 숫자를 포함하는 range객체를 만들어준다.

for number in numbers:
    if number % 2 == 1:
        print(number)

1
...
29

# 1~30까지 숫자 중에서 홀수를 모아서 리스트로 출력

numbers = range(31)
result = []

for number in numbers:
    if number % 2 == 1:
        result.append(number)
        
print(result)

[1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29]
```

```python
menus = ['불닭', '닭발', '곱창', '미역국', '산적']

for menu in menus:
    print(menu)

# 위와 똑같은 코드를 다른 방식으로 작성

for i in range(len(menus)):
    print(menus[i])

# enumerate 함수

for item in enumerate(menus):
    print(item)

(0, '불닭')
(1, '닭발')
(2, '곱창')
(3, '미역국')
(4, '산적')

for index, menu in enumerate(menus):
    print(index, menu)

0 불닭
1 닭발
2 곱창
3 미역국
4 산적
```
#### 2.2.2 dictionary 반복
-  for key in dict: 
-  for key in dict.keys(): 
-  for value in dict.values(): 
-  for key, value in dict.items(): <br/><br/>

```python
#  for key in dict:

info = {
    'name': 'tina',
    'location': 'seoul',
    'phone': '010-1234-1234',
}

for key in info:
    print(key)
    print(info[key])


# for key in dict.keys():

blood_type = {
    'A': 5,
    'B': 4,
    'O': 2,
    'AB': 3,
}
for key in blood_type.keys():
    print(key)

A
B
O
AB


# for value in dict.values():

for value in blood_type.values():
    print(value)

5
4
2
3

# for key, value in dict.items():
# 키와 밸류가 같이 필요할 때 

for item in blood_type.items():
    print(item)

('A', 5)
('B', 4)
('O', 2)
('AB', 3)
```

#### 2.2.3 for문에서 break로 반복문 끝내기

```python
for i in range(100):
    print(i)
    if i > 10:
        print('10 넘었어!!!')
        break

0
1
2
3
4
5
6
7
8
9
10
11
10 넘었어!!!

rice = ['보리', '보리', '보리', '보리', '쌀', '보리', '보리', '보리', ]
# 보리 보리 보리 보리 쌀 잡았다!

for r in rice:
    print(r)
    if r == '쌀':
        print('잡았다')
        break

보리
보리
보리
보리
쌀
잡았다
```

#### 2.2.4 for문에서 continue로 코드 실행 건너뛰기
- continue 이후의 코드를 실행하지 않고 다음 반복을 실행한다.

```python
for i in range(10):
    if i % 2:
        continue

    print(i)

0
2
4
6
8

age = [10, 23, 8, 30, 29, 15]
for a in age:
    if a < 20:
        continue
    print(f'{a}살은 성인입니다.')

23살은 성인입니다.
30살은 성인입니다.
29살은 성인입니다.
```

#### 2.2.5 for ~ else ~ 문
-  for문을 돌면서 for문 내부에서 break를 만나지 않았을 때의 동작을 제시

```python
for i in range(12):
    print(i)
    if i > 10:
        break

else:
    print('break 못만남')

0
1
2
3
4
5
6
7
8
9
10
11


numbers = [1, 2, 3, 4, 5]
target = 5

# numbers를 반복하다 target이 있으면 True 출력 없으면 False출력
for number in numbers:
    if number == target:
        print('True')
        break
else:
    print('False')

True
```
### 2.3. match 함수
```python
match value:
    case 조건:
        실행할 코드
    case 조건:
        실행할 코드
    case _:
        실행할 코드
```

```python
status = 100

match status:
    case 400:
        print('bad request')
    case 404:
        print('not found')
    case _:
        print('something is wrong')

something is wrong
```