---
layout: post
title: '리스트와 반복문(list / for)'
comment: true
categories: 'python'
tag:
 - content
 - python
 - basic
 - list
 - Series
 - for
---

# 리스트의 사용
 ```
 L1 = [1,2,3,4,5]

 L1[1:4]     # 슬라이드 색인 
 L1[[1,3]]   # 벡터 색인(여러 값을 묶어 색인값으로 전달)
 L1==2       # 비교 불가
 L1 + 2      # 연산 불가

 list(map(lambda x : x < 2, L1))     # (T/F 만 출력) map 함수 사용해 각 원소별 비교  
 L1[list(map(lambda x : x < 2, L1))] # 조건색인 불가 (조건의 결과를 갖는 리스트를 색인값으로 전달받을 수 없다.)
 ```

## Series in Python
  * DF에 컬럼을 구성하는 요소(같은 타입만 허용)
  * Series에 문자열 처리(split, replace...) 직접 적용 불가  

 ```
 from pandas as Series
 s1=Series([1,2,3,4,5])
 
 s1[[1,3]]  # 벡터 색인 가능 (= 여러개 묶어서 색인)
 s1 < 2     # 조건 전달 가능
 s1[s1<4]   # 조건 색인 가능 
 s1 + 1     # 벡터연산 가능= Series([1,2,3,4,5])
 ```
  
1.`리스트 주요 메서드`  

 ```
 L1 = [1,2,3,4,5]
 L2 = [1,5,2,3,4]

 ## 원소 추가
 L1.append(6) ; L1    # 원소 추가 (값이 들어간다)
 L1.extend([7]) ; L1  # 원소 추가 (List 확장으로 추가된다)
 L1.insert(0,10); L1  # 0번째 위치에 10 삽입

 ## 원소 제거
 L1.remove(3) ; L1  # 특정 원소 삭제
 L1.pop(); L1       # 마지막 원소 삭제

 ## 카운트
 L1.count(1)        # 원소 포함 횟수

 L1.index(4)        # 원소 위치
 L1.index(3)        # 원소에 값이 없을 경우 에러 출력  / find, 없을경우 -1 출력
 

 L2.sort(reverse=False) ;L2 # 정렬된 결과 추출, 즉시 반영

 len(L1)   # 리스트 사이즈 (원소 갯수)
 ```

## for문
 ```
 for i in range(0,6) : 
    print(i)

for i in range(0,6,2) :
    print(i)
    
for i in L1 : 
    print(i)

for i in L1 :
    print(i, end ='') #print의 end값 없으므로 일렬로 출력
 ```

1. `중첩 for문`
 ```
 L1 = [1,2,3]
 L2 = [[1,2,3],[4,8,45],[71,80,19]]

 for i in L1 :
     print(i, end = ' ')

 for i in L2 :
     print(i, end = ' ')

 for i in L2 :
     for j in i:              # 1. 리스트를 묶은 i(1,2,3) j에 할당 (4.반복)
         print(j, end = ' ')  # 2. 원소 분리 , => ' '
     print()                  # for문 끝난 다음 출력 3.줄바꿈

 ```
2.`위치값 기반`
 ```
  # 위치값 기반
 for i in range(0,3):
     for j in range(0,3) : 
         print(L2[i][j], end = ' ')
     print()
 ```

## [while문](https://docs.python.org/3/tutorial/controlflow.html)
 ```
 i=0
while i < 11:
    print(i)
    i = i + 1
 ```
 * 예제) 1-100까지 짝수 합 출력
 ```
 1.기본 while 구문
 vsum=0; i=1
 while i < 101:
    if i % 2 == 0:
        vsum += i
    i += 1
 print(vsum)
 
  # 2. continue구문
 vsum = 0; i = 0
 while i < 101:
     i += 1
     if i % 2 != 0:
         continue   # R에서의 next구문과 동일
     vsum += i
 print(vsum)
 ```