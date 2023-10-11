# 1. 문자열 메소드

- 메소드란? 객체안에 들어있는 함수를 말한다.
- 메소드는 a라는 객체가 존재할 때 a.upper(), a.lower()와 같은 형태로 사용된다.

```python
# 문자열 데이터 바꾸기
a = 'hello my name is tina'
print(a)

hello my name is tina

print(a[0])

h

a[0] = 'H'
TypeError: 'str' object does not support item assignment
# string은 immutable하기 때문에 0번째 데이터를 바꾸려면 수정이 불가능하다. 따라서 데이터를 바꾸려면 덮어씌워줘야한다.
# a = 'Hello my name is tina'
```
<br/>

- `str.capitalize()` : 맨 첫글자만 대문자로 변환
- `str.upper()` : 모든 알파벳을 대문자로 변환
- `str.title()` : 알파벳 외의 문자로 나누어져 있는 알파벳의 첫 글자를 대문자로 변환
- `str.lower()` : 모든 알파벳을 소문자로 변환

```python
a.capitalize()
'Hello my name is tina'

a.upper()
'HELLO MY NAME IS TINA'

a.title()
'Hello My Name Is Tina'

a.lower()
'hello my name is tina'
```
<br/>

- `str.join(iterable)` : 리스트에 담긴 문자열을 연결.
```python
my_list = ['hi', 'my', 'name']
'??'.join(my_list)

'hi??my??name'
```
<br/>

- `str.strip([chars])` : 문자열 내에서 원하는 문자열 또는 공백을 모두 제거한다.
```python
# 공백을 제거할 때 
my_string = '     hello\n   '
print(my_string.strip())

hello

# 원하는 문자열을 제거할 때
my_string2 = 'hihihihihihihihellohihihihihihihi'
print(my_string2.strip('hi'))

ello

# 원하는 문자열에서 왼쪽만 제거하고 싶을 때
# .lstrip()
print(my_string2.lstrip('hi'))

ellohihihihihihihi

# 원하는 문자열에서 오른쪽만 제거하고 싶을 때
# .rstrip()
print(my_string2.rstrip('hi'))

hihihihihihihihello
```
<br/>

- `str.replace(old, new[, count])` : 문자열에서 변경하고 싶은 문자를 [횟수]만큼 변경.
```python
# str.replace('변경하고 싶은 문자', '변경 후 문자', 횟수)

a = 'wooooooooow'
a.replace('o', '!', 3)

'w!!!oooooow'
```
<br/>

- `str.find()` : "찾을 문자" 혹은 "찾을 문자열" 존재하는지 확인하고,<br/>
 **찾는 문자가 존재 한다면 해당 위치의 index를 반환해주고<br/> 찾는 문자가 존재 하지 않는다면 `-1` 을 반환.** 
 ```python
# str.find(찾을 문자)
# str.find(찾을 문자, 시작 Index)
# str.find(찾을 문자, 시작 Index, 끝 Index)

a = 'apple'
a.find('p')

1

a.find('z')

-1

# find 메소드를 구현한 for함수
for i in range(len(a)):
    if 'p' == a[i]:
        print(i)
        break
else:
    print(-1)
```
<br/>

- `str.index(x)` : 지정요소의 위치의 index를 반환. **여러개인 경우 가장 첫번째** 것만 반환하며 **찾는게 없을 경우 에러 발생**.
```python
a = 'apple'

print(a.index('p'))
print(a.index('z'))

1
ValueError: substring not found
```
<br/>

- `str.split()` :  문자열을 일정한 규칙으로 잘라서 리스트로 변환.

```python
# 문자열.split(seq='구분자', maxsplit=분할 횟수)
a = 'hello_my_world'
print(a.split('_'))

# 구분자를 기준으로 split
['my', 'name', 'is']
```
<br/>

- `str.count(x)` : 문자열 내부에서 특정 문자, 문자열이 포함되어있는지 계산해서 반환.

```python
'wooooooow'.count('o')
7
```

<br/><br/>

# 2. 리스트 메소드

- `.append(x)`: 기존 리스트의 마지막 위치에 값을 추가.
- `.insert(x)`: 기존 리스트에 인덱스로 지정한 위치에 값을 추가.
- `.extend(x)`: 기존 리스트에 다른 리스트를 연결하여 확장하면서 값을 추가. 

```python
# .append(x)
# 뒤에 값을 추가할 때
numbers = [1, 5, 6, 4, 1, 2]
numbers.append(10)
print(numbers)

[1, 5, 6, 4, 1, 2, 10]

# .insert(idx, x)
# 특정한 위치가 필요할 때 
numbers.insert(3, 3.5)
print(numbers)

[1, 5, 6, 3.5, 4, 1, 2]

# .extend(x)
# 확장하다
a = [99, 100]
numbers.extend(a)
print(numbers)
print(numbers + a)

[1, 5, 6, 4, 1, 2, 99, 100]
[1, 5, 6, 4, 1, 2, 99, 100, 99, 100]
```
<br/>

- `.remove(x)`: 리스트에서 원하는 값을 찾아서 삭제.
- `.pop()`: 리스트에서 특정 인덱스의 요소를 삭제.

```python
# .remove(x)
numbers = [1, 5, 6, 3.5, 4, 1, 2]
numbers.remove(3.5)
print(numbers)

[1, 5, 6, 4, 1, 2]

# .pop()
# 맨 마지막에 있는 데이터만 빼냄
numbers.pop()
print(numbers)

[1, 5, 6, 4, 1]

# .pop([idx]) 원하는 인덱스값으로 원하는 데이터만 빼낼 수 있음.
numbers.pop(0)
print(numbers)

[5, 6, 4, 1, 2]
```
<br/>

- `.sort()`: 리스트를 오름차순으로 정렬해주는 기능
    - 새로운 정렬된 리스트를 반환하는것은 sorted 함수
    - 리스트 자체를 정렬시켜버리는것은 sort 메소드
- `.sort(reverse=True)`: 리스트를 내림차순으로 정렬
- `.reverse()`: 정렬은 아니지만 리스트 안에 내용을 뒤집을 때

```python
# .sort()
numbers = [1, 6, 2, 1, 3, 2, 7, 10]
print(numbers.sort())
print(numbers)

None
[1, 1, 2, 2, 3, 6, 7, 10] # 원본 데이터를 정렬데이터로 sort

# sort(reverse=True) 역정렬
numbers.sort(reverse=True)
print(numbers)

[10, 7, 6, 3, 2, 2, 1, 1]

# sorted (sort처럼 데이터를 가지고 있는게 아님) 
print(sorted(numbers))

[1, 1, 2, 2, 3, 6, 7, 10]

# .reverse()

numbers = [1, 6, 2, 1, 3, 2, 7, 10]
numbers.reverse()
print(numbers)

[10, 7, 2, 3, 1, 2, 6, 1]

numbers = numbers[ : :-1] #슬라이싱을 통해서도 구현이 가능하다.
print(numbers)
```
<br/>

## 2.1. list copy

일반적으로 리스트를 copy할 때 아래와 같은 형식으로 진행된다.

```python
# 실제로 list는 1개만 존재하지만 origin_list, copy_list 두가지 이름이 존재한다.
origin_list = [1, 2, 3]
copy_list = origin_list

print(origin_list)
print(copy_list)

[1, 2, 3]
[1, 2, 3]


# .deepcopy() - 깊은 복사(리스트안에 또 리스트가 있는 경우)
import copy
a = [1, 2, [99, 100]]
b = copy.deepcopy(a)

b[2][1] = 1000

print(a)
print(b)

[1, 2, [99, 100]]
[1, 2, [99, 1000]]
```
<br/>

## 2.2. list comprehension (리스트 표현식)
- 리스트 안에 식, for 반복문, if 조건문 등을 지정하여 리스트를 생성하는 것


```python
# [1, 8, 27... 1000] => 세제곱 만들기

# 첫번째 방법
# 반복처리하면서 하나하나 세제곱시키고 리스트에 하나하나씩 추가하는 방법
numbers = list(range(1, 11))
result = []

for number in numbers:
    result.append(number ** 3)
print(result)

# 두번째 방법
# list comprehension
result2 = [ number ** 3 for number in numbers ]
print(result2)

# 짝수만 고르기 (for문과 if문을 응용)
numbers = list(range(1, 11))
even_list = []
for number in numbers:
    if number % 2 == 0:
        even_list.append(number)
print(even_list)

[2, 4, 6, 8, 10]

# list comprehension
even_list2 = [number for number in numbers if number % 2 == 0]
print(even_list2)

[2, 4, 6, 8, 10]
```
```python
# 문제 풀이
words = 'my name is hong'
vowels = 'aeiou'

# => my nm s hng (모음을 뺀 단어)

# 1. for문

result = []

for char in words:
    if char not in vowels:
        result.append(char)
print(result)
print(''.join(result))

['m', 'y', ' ', 'n', 'm', ' ', 's', ' ', 'h', 'n', 'g']
my nm s hng

# 2. list comprehension

result2 = [char for char in words if char not in vowels]
print(result)
print(''.join(result))

['m', 'y', ' ', 'n', 'm', ' ', 's', ' ', 'h', 'n', 'g']
my nm s hng
```
<br/><br/>

# 3. 딕셔너리 메소드

- `.pop(key[, default])`: 딕셔너리에서 특정 키-값 쌍을 삭제한 뒤 삭제한 값을 반환.
```python
# .pop(key[, default])
# 데이터를 제거할 때

info = {
    'name': 'tina',
    'location': 'seoul',    
}

print(info)
print(info.pop('location'))

# pop은 기본적으로 데이터를 제거하고 어떤 데이터를 제거했는지 나타내는데, 제거했는데 그 데이터가 없다면 사용자가 지정해서 표시해줄 수 있음.
print(info)
print(info.pop('location', None))

```
<br/>

- `.update(key=value)`: update(키=값)은 이름 그대로 딕셔너리에서 키의 값을 수정

```python
# .update(key=value)
info.update(name='park')
print(info)
```
<br/>

- `.get(key[, default])`: 딕셔너리에서 특정 키의 값을 가져옴.
    - **get(키, 기본값)** 처럼 기본값을 지정하면 딕셔너리에 키가 있을 때는 해당 키의 값을 반환하지만 키가 없을 때는 기본값을 반환

```python
# .get(key[, default]) #접근
print(info.get('name')) 
print(info.get('phone')) # None 값 도출
print(info.get('phone', '해당키가 없습니다'))

```

## 3.1 dict comprehension

```python
# for문
# {1: 1, 2: 8, 3: 9...}
result = {}
numbers = range(1, 11)
for number in numbers:
    result[number] = number ** 3

print(result)

# comprehension
result2 = { number : number ** 3 for number in range(1, 11)}
print(result2)
```

```python
# 문제풀이

dust = {
    '서울': 100,
    '대구': 30,
    '부산': 50,
    '광주': 80,
    '제주': 20,
}

# result = {
#    '서울': 100,
#    '부산': 50,
#    '광주': 80,
#}


# 1. for문
result = []
for k, v in dust.items():
    if v >= 50:
        result[k] = v

print(result)

{'서울': 100, '부산': 50, '광주': 80}

# 2. comprehension
result2 = { k: v for k, v in dust.items() if v >= 50}
```
<br/><br/>

# 4. 세트 메소드

- `.add(x)`: 세트에 요소를 추가

```python
# 순서가 없는 집합이라 순서는 뒤죽박죽
fruits = {'apple', 'banana', 'melon'}
fruits.add('grape')
print(fruits)
fruits.add('grape') # 두번 더해줘도 하나만 보임. 
print(fruits)

{'banana', 'grape', 'apple', 'melon'}
{'banana', 'grape', 'apple', 'melon'}
```

- `.update({set})`: 집합의 값을 한번에 **여러개** 추가

```python
fruits.update('watermelon')
print(fruits)

{'e', 'n', 't', 'o', 'apple', 'm', 'a', 'melon', 'r', 'l', 'banana', 'w'}

# 단어 온전히 의도한대로 넣으려면
fruits.update({'watermelon', 'orange'})
print(fruits)

{'e', 'n', 't', 'o', 'apple', 'm', 'a', 'melon', 'r', 'l', 'watermelon', 'banana', 'orange', 'w'}
```
- `.remove(x)`: 세트에서 특정 요소를 삭제하고 요소가 없으면 에러를 발생

```python
fruits.remove('orange')
print(fruits)
```
- `.pop()`: 세트에서 임의의 요소를 삭제하고 해당 요소를 반환. 만약 요소가 없으면 에러를 발생

```python
fruits.pop()
print(fruits)
```
<br/><br/>

### map, filter, zip

- `map(function, iterable)`
```python
a = [1, 2, 3]
number_str = map(str, a) # 첫번째 인자로는 함수를 집어넣고 그 뒤에 시퀀스형 객체를 집어넣음. 그 결과를 변수에 저장한다.
print(number_str)  
print(list(number_str))

<map object at 0x00000189CEE018A0> # 변환하는 순간 출력
['1', '2', '3']

# for문
result = []
for i in a:
    result.append(i ** 3)

print(result)

[1, 8, 27]

# 예제 함수 
def cube(x):
    return x ** 3

print(cube(5))
print(cube(10))

125
1000

# 함수를 인자로 넣고 a를 반복처리하면서 cube처리
result2 = map(cube, a)
print(list(result2))

[1, 8, 27]

# 예제
a = '1 3 5 7 9'
# result = [1, 3, 5, 7, 9]

numbers = list(map(int, a.split()))
print(numbers)

[1, 3, 5, 7, 9]
```

- `filter(function, iterable)`
    - Filter에 들어가는 function은 True, False를 반환해야 합니다

```python

# 자연수가 홀수인지 짝수인지 판별해 주는 함수(is_odd)
def is_odd(x):           
    if x % 2 == 1:
        return True
    else:
        return False

print(is_odd(5))
print(is_odd(10))

True
False

# 위를 간결하게
def is_odd(x):
  return bool(x % 2)

print(is_odd(5))
print(is_odd(10))

True
False

# 홀수들만 출력
numbers = [1, 2, 3, 4, 5]

# for문
result = []
for number in numbers:
    if is_odd(number):
        result.append(number)

print(result)

[1, 3, 5]

result2 = filter(is_odd, numbers)
# 레이지한 연산이기 때문에 바로 출력이 안되서 list형태로 바꿔줘야됌.
print(list(result2))

[1, 3, 5]
```

- `zip`

```python
a = [1, 2, 3, 4]
b = [100, 200, 300, 400, 500]

result = zip(a, b) # zip도 레이지한 연산 zip을 통과하자마자는 메모리주소만 출력됌.
print(result)
print(list(result)) # 두개의 리스트를 한 쌍으로 사용해야될 때 단, 갯수가 맞아야됌.

<zip object at 0x00000189CF1F5640>
[(1, 100), (2, 200), (3, 300), (4, 400)]
```