---
layout: post
categories: python
title: '리스트 컴프리헨션(list comprehension)2'
order: 5
comment: true
tag:
 - python
 - basic
 - list
 - list comprehension
---
 
# [리스트 컴프리헨션(list comprehension)](https://python-reference.readthedocs.io/en/latest/docs/comprehensions/list_comprehension.html)
- 리스트 내포 표현식
- 리스트가 벡터 연산이 안되는 점을 비교적 간단한 문법으로 가능하게 함.
- 리스트 내부에 반복/조건문의 축약형 형태 전달 가능
- 되도록 2번 이상 중첩하지 않을 것.(중첩할 수록 보기 어려워 진다.)

1.`문법`
```
[리턴 for i(반복변수) in 대상]
[리턴 for i(반복변수) in 대상 if 조건]
[참리턴 if 조건 else 거짓리턴 for i(반복변수) in 대상]
- 중첩일 경우 : [[후행] for i(반복변수) in 대상-선행]
ex) [[_-1 for _ in i ]for i in list]
[[0, 1, 2], [3, 4, 5], [6, 7, 8]]
```


* 예제1) 아래 리스트에 10% 인상된 값 리턴

 ```
 L1 = [1,2,3,4,5]
 
 ## for문
 L2=[]
 for i in L1:
    L2.append(i * 1.1)
    
 ## mapping
 list(map(lambdax x : x * 1.1, L1))
 
 ## list comprehension
 [i * 1.1 for i in L1]    
 ```

 * 예제2) 아래 리스트에서 3보다 작은 값만 출력

```
L1=[1,2,3,4,5]

## for문
l2=[]
for i in L1:
    if i < 3:
        l2.append(i)
        
 ## mappint
 f1 = lambda x : x if x < 3 else None # 람다는 if full문법 불가, else 생략 불가
 list(map(f1,L1))
 
 ## 리스트 컴프리헨션
 [i for i in L1 if i < 3]            # 조건이 있을때 조건만 출력
 [i for i in L1 if i < 3 else i * 3] # 불가
```

# 연습문제
```
sal = ['9,900','25,000','13,000']
addr = ['a;b;c','aa;bb;cc','aaa;bbb;ccc']
comm = [1000,1500,2000]
```
 # 예제1) sal의 10% 인상값 출력  
<div style="color:white">
## for문<br>
outlist=[]<br>
for i in sal:<br>
 &nbsp;    outlist.append(round(int(i.replace(',','')) * 1.1, 1))<br>
outlist
<br>
<br>
## mapping<br>
list(map(lambda x : round(int(x.replace(',',''))*1.1,1),sal))
<br>
<br>
## list comprehension<br>
[int(i.replace(',','')) *1.1 for i in sal]
</div>

 # 예제2) addr에서 각 두번째 값(b, bb, bbb) 출력  
<div style="color:white">
## for문<br>
outlist=[]<br>
for i in sal:<br>
 &nbsp;    outlist.append(i.split(';')[1])<br>
outlist
<br>
<br>
## mapping<br>
list(map(lambda x : x.split(';')[1],addr))
<br>
<br>
## list comprehension<br>
[i.split(';')[1] for i in addr]
</div>

```
[참고 - map에 인자 전달 방식]
f1 = lambda x , y: x.split(';')[y]
list(map(f1,addr,1))
 # 'int' object is not iterable, (1)에서 에러 - map에 숫자 전달 불가

list(map(f1,addr,[1]))  
# b만 출력 (addr,3과 [],1의반복 횟수가 일치하지 않아 앞만 전달)
# addr과 [1]의 반복횟수 불일치, 1번만 반복

list(map(f1,addr,[1,1,1]))
# addr과 반복횟수 맞춰서 전달 필요
```
