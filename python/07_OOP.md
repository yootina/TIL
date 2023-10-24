# 객체지향 프로그래밍(OOP)

- 클래스(class) : 같은 종류의 집단에 속하는 속성(attribute)과 행위(method)를 **정의**한것
- 인스턴스(instance) : 클래스를 실제로 메모리상에 할당한것
- 속성(attribute) : 클래스/인스턴스가 가지고 있는 데이터/값
- 행위(method) : 클래스/인스턴스가 가지고 있는 함수/기능

## 클래스(class)
```python
# 클래스를 선언한다
class ClassName:
    attribute = value

    def method_name(self):
        code

# 인스턴스화
ClassName()
```

```python
class Person:
    name = '사람'
    email = 'xxx@XXX.com'

    def greeting(self):
        print('Hello')

    def eat(self, food):
        print(f'배고파서 {food}을 먹는다.')

jane = Person()
print(type(jane))

jane.name = '제인'
print(jane.name)
jane.greeting()

nick = Person()
print(type(nick))

nick.name = '닉'
print(nick.name)
nick.email = 'aaa@AAA.com'
print(nick.email)

nick.eat('사과')

<class '__main__.Person'>
제인
Hello # jane.greeting을 호출하니 'Hello'가 출력
<class '__main__.Person'>
닉
aaa@AAA.com
배고파서 사과을 먹는다. # nick.eat('사과')를 호출하니 메세지가 출력 >> 인스턴스 메소드

# jane과 nick은 서로 완전히 독립된 다른 객체를 가지고 있음.
```

