---
layout: post
title: '중첩 for문 (nested for loop)과 튜플(tuple)'
comment: true
order: 4
categories: 'python'
tag:
 - content
 - python
 - basic
 - nested for
 - tuple
 - dict
---
 
# 중첩 for문을 이용한 리스트의 입출력

 ```
 L1 = [[1,2,3],[4,5,6],[7,8,9]]
 
 ## 입력    
 z = 1;outlist=[]
 for i in range(0,3):
     inlist = []        #초기화 시키기 위해 빈 리스트 내부에 삽입
     for j in range(0,3):
         inlist.append(z)
         z += 1
     outlist.append(inlist)
 outlist

 ## 출력
 z = 1
 for i in range(0,3):
     for j in range(0,3):
         print(z,end = ' ')
         z += 1
     print()
 ```

 * 예제1) 0부터 3씩 증가하는 4 * 5 형태의 중첩 리스트 출력  
 
 ```
 list1=[]
 list2=[]
 value=1
 
 for i in range(0,3):
    for j in range(0,3):
        list1.appned(value)
        value += 3
    list2.appen(list1)
    list1=[]
    
 [[1, 4, 7]]
 [[1, 4, 7], [10, 13, 16]]
 [[1, 4, 7], [10, 13, 16], [19, 22, 25]]

##
 z=0 
 for i in rnage(0,4):
    for j in range(0,5):
        print('%2d'%z, end=' ')
        z += 3
    print() 
    
  0  3  6  9 12 
 15 18 21 24 27 
 30 33 36 39 42 
 45 48 51 54 57 

 ```

# 튜플(tuple)
 - 읽기 전용 리스트
 - 리스트와 동일한 자료구조(1차원, 서로 다른 데이터 타입 허용)
 - 수정 불가(읽기 전용)
 - 수정되면 안되는 참조 생성시 필요
 - 소괄호() 또는 쉼표로 생성

1.`생성`
 ```
 t1=(1,2,3)
 t2=1,2,3
 t3=(10,)
 t4=(10)

 type(t1)  # tuple
 type(t2)  # tuple
 type(t3)  # tuple
 type(t4)  # int
 ```

2.`수정`
```
t1[0] = 10    # 'tuple' object does not support item assignment
t1.append(11) # 불가
del(t1[0])    # 삭제 불가
del(t1)       # 전체 삭제는 가능

```

# 딕셔너리(dict)
- R에서 리스트와 비슷
- {key : value} 형식
- Series, DataFrame의 기본 구조

1.`생성`
```
d1 = {'a':1,'b':2}
d2 = {'a':[1,2], 'b':[3,4]}
type(d1)   # dict
```

2.`색인`
- key 색인 가능
```
d1['a']
d1.get('a')  # 
```

3.`수정`
```
d1['b']=22
d1['c']=3  # 없는 값도 전달 가능
```

4.`삭제`
```
del(d1['c'])
d1['b']=NA  # from numpy import nan as NA, nan으로 표시된다.
```

5.`딕셔너리 키 출력`
- set(d1)  

```
set(d1)
{''c','a'}

# 참고 - dict와 Series, DataFrame 관계
from pandas import Series
from pandas import DataFrame

Series(d2)     # dict의 키가 인덱스로 변환
a    [1, 2]
b    [3, 4]

DataFrame(d2)  # dict의 키가 컬럼으로 변환
   a  b
0  1  3
1  2  4

## 인덱스 값 전달받을 대상(key) 없으므로 0 1 2로 표시
Series([1,2,3]) 
0    1
1    2
2    3

## DF로 전달시 {} 묶음
DataFrame({'a' :[1,2,3], 'b':[4,5,6]})
   a  b
0  1  4
1  2  5
2  3  6
```

* 연습)다음의 리스트와 딕셔너리를 참고해 전화번호를 완성, 02)345-4958
 ```
 l1 = ['345-4958','334-0948','394-9050','473-3853']
 l2 = ['서울','경기','부산','제주']
 area_no = {'서울':'02', '경기':'031','부산':'051','제주':'054'}
 ```
<div style="color:white">area_no.get(l2[0]) + ')' +l1[0]
</div>
<div style="color:white">area_no.get(l2[1]) + ')' +l1[1]
</div>
<br>

<div style="color:white">f1 = lambda x, y : area_no.get(y) + ')' + x
</div>
<div style="color:white">list(map(f1,l1,l2))
</div>