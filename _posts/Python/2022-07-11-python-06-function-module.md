---
layout: post
categories: python
title: '함수와 모듈'
order: 6
comment: true
tag:
 - python
 - basic
 - module
---
 
# 함수 기본
 - 함수(Function) : '무엇'을 넣으면 '결과'를 돌려주는 상자라고 하자.
 - 메서드(method)와 차이점 : 함수는 외부에 별도로 존재, 메서드는 클래스 내부에 존재
 ```
 함수명()
 ```

## 함수 정의하기
 - 함수는 def 키워드를 이용해 코드블록에 이름을 붙인 형태  
 ```
 def 함수명(매개변수 목록):
 # 코드블록
 return 결과
 ```

 * 예제) plus 함수를 만들어보자

```
## 함수 선언부
def plus(v1, v2):
   result = 0
   result = v1 + v2
   return result

 ## 전역 변수 선언부
 hap=0
 
 ## 메인 코드부
  hap=plus(100,200)
  print('100과 200dml plus() 함수 결과는 %d' % hap)
  
100과 200의 plus() 함수 결과는 300
```

## 재귀 함수
 - 자기 자신을 호출하는 함수
```
def selfcall():
   print('하', end='')
   selfcall()
selfcall()
```

 - 팩토리얼(Factorial)값을 구하는 함수
```
def factorial(num):
   if num <= 1:
      return num
   else:
      return num * factorial(num - 1)
print(factorial(4))
> 24
print(factorial(10))
> 3628800
```

## 지역변수와 전역변수
 - 지역 변수 : 한정된 부분에서만 사용
 - 전역 변수 : 프로그램 전체에서 사용


```
## 지역 변수
def fun1():
    a=10  # 지역 변수, func1 함수에서만 사용
    print('func1()에서 a값 %d' %a)

"func1()에서 a값 10"

## 전역 변수
def func2():
    print('func2()에서 a값 %d' %a)
a=20   # 전역 변수, 프로그램 전체에 지정

"func2()에서 a값 20"


## global 예약어
def func3():
    global a   # global에 할당된 변수는 전역 변수가 된다.
    a=10
    print('func3()에서 a값 %d' %a)

"func3()에서 a값 10"

def func4():
    print('func2()에서 a값 %d' %a)
a=20   # 전역 변수, 프로그램 전체에 지정
   
"func4()에서 a값 10"    
```

# 모듈
 - 모듈 : 함수의 집합

* 모듈의 생성과 사용
```
def func1():
    print('Module1.py의 func1()이 호출됨.")
    
def func2():
    print('Module2.py의 func2()이 호출됨.')
```

* 모듈명을 생략하고 함숨명만 쓸 때 1행 형식
```
from 모듈명 import 함수1, 함수2, 함수3
or
from 모듈명 import * 
```

1.`모듈의 종류`
 - 표준 모듈, 사용자 정의 모듈, 서드 파티 모듈로 구분
 - 표준 모듈 : 파이썬에서 제공하는 모듈
 - 사용자 정의 모듈 : 직적 만들어서 사용하는 모듈
 - 서드 파티(3rd party) 모듈 : 파이썬이 아닌 외부 회사나 단체에서 제공하는 모듈
   - 파이썬 표준 모듈이 모든 기능을 제공하지 않음.
   - 서드 파티 모듈덕에 파이썬에서도 고급 프로그래밍 가능
   - 게임 개발 기능이 있는 pyGame, 윈도창을 제공하는 PyGTK, 데이터 베이스 기능의 SQLAlchemy 등

* 파이썬에서 제공하는 표준 모듈의 목록을 일부 확인
```
import sys
print(sys.builtin_module_names)

import math
dir(math)
```