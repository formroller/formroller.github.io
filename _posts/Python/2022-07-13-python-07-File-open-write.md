---
layout: post
categories: python
title: '파일에 데이터 읽고 쓰기'
order: 7
comment: true
tag:
 - python
 - basic
 - file
 - open
 - write
---

# 파일 입출력의 기본
1. 외부파일 불러오기
```
open : 파일을 열어 메모리상으로 불러오는 작업
fetch : 선언된 cursor(임시 메모리 공간)에 저장된 data를 한 건씩 불러고이
close : 객체 선언 완료 후 cursor에 할당된 메모리 영역 close
        cursor 닫지 않으면 메모리 누수 현상이 발생할 수 있으므로 주의
```

* 예시) 

```
c1 = open('read_test1.txt')  # 커서 선언
v1 = c1.readline()  # readline, 한 줄씩 가져온다.
c1.close()

## 불러오기 모드(mode) 설정
c1 = open('read_test1.txt', 'r') # 모드 설정 가능(r/w)
```
 
* 텍스트 파일 입출력

```
## 한 행씩 입출력
inFp = None  # 입력 문자
inStr = ""   # 읽어 온 문자열

inFp = open(path, 'r')
print(inStr, end='')

## 모든 행 읽기
inFp = None  # 입력 파일
inStr= ""    # 읽어 온 문자열

inFp=open(path,'r')

while True:
    inStr=inFp.readline()
    if inStr == "":
        break;
    print(inStr, end="")
    
inFp.close()

## 한 번에 모두 읽어 들이기
 - readlines()함수 : 파일의 내용을 통째로 읽어서 리스트에 저장
inFp = None
inList=""

inFp = open(path, 'r')

inList=inFp.realines()
print(inList)

inFp.close()
```


* 참고
  * 프로그램 생성하다보면 close() 함수를 호출하지 않고 프로그램을 종료해 문제가 종종 발생한다.\
  아예 close() 함수를 사용하지 않으려면 *with~as*문으로 파일을 연다.
  ```
  with open(path,"r") as inFp:
    inList = inFp.readlines()
    print(inList)
  ```