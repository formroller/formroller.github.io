---
layout: post

title: "문자열(string)" 

comments: true

categories:

  - python

tags:

  - content

  - Python

  - basic

  - string
---
# print 함수
```
print(1) 1출력
print('%d' % 1)        	# 정수 형식 출력 (%d)
print('%f' % 10)  	  # 실수 형식 출력 (%f)
print('%s' % 'abcde')     # 문자열 형식 출력 (%s) 
```
# 색인(Indexing)
파이썬은 위치값이 0부터 시작한다. 
```
 v1='abcdefg'일때
 v1[1] (문자열 색인 가능-R에서는 불가)) 
 'b'
 v1[1:2] (첫 번째부터 두 번째 전까지 추출-끝 범위 다음 번호 추출해야한다.)
 'b'
 v1[1:3]
 'bc'
 ```
# escape 문자
```
print('\')  # 출력 오류
> SyntaxError: EOL while scanning string literal
print('\\') # '\'를 일반 기호화하기 위해 백슬래쉬 사용
> '\'
print('a\nc')   
>>a
  c
```
# .format
{0:d} {1:5d} {2:0d} -> {자릿수:포맷}
```
 print('%d %5d %05d' % (123, 123,123))
>> 123,  123,00123 -> %5d일 경우 공백 포함해 5자리로 생성
``` 


# 문자열 사용
```
v1 = 'select ename </br> 
      from emp'
```
위 코드의 경우 enter(\<br>) 삽입으로 인해 에러가 발생한다.  
따라서 enter 삽입시 \`\`\`  \`\`\`\`로 묶어야 한다.


1. `문자열 포함 여부`
    ``` 
      1. 'a' in 'abcd', True
      2. 'abcd' in 'a', False
      * '찾을 문자' in '문자열'
    ```


2. [`startswith 함수`](https://www.w3schools.com/python/ref_string_startswith.asp)
   1. a.startswith : 문자열이 지정된 값으로 시작하면 True, 아닐 경우 False 출력
    ```
    a1='abcde'
    a1.startswith(suffix, # 시작값
                  start,  # 검사 시작 위치
                  end     # 검사 끝 위치
                  )
    a1.startswith('a',1)   # a1의 두번째 글자가 'a'로 시작하는지 묻는다.
    a1.startswith('a',1,3) # a1[1:3] 'a'로 시작하는지 묻는다.  
   
    (startswith와 반대로 지정된 값으로 끝나는지 확인하는 endswith가 있다.)
   ```

3. `strip`
   1. 공백 제거함수이며, 방향에 따라 'l/rstrip' 또는 'strip'으로 사용한다.
   ```
   a2 = '   abc   ' 
   a2.lstrip()    # a2 왼쪽 공백 제거
   >> 'abc   '
   a2.lstrip('a') # 문자 제거 가능 (단, 가운데 문자는 제거 불가)   
   a2.rstrip()    # a2 오른쪽 공백 제거 
   >> '   abc'
   a2.strip()
   >> 'abc'
   ```
4. `replace`
   1. 문자열 내 단어를 변환한다. 
   ```
   a1.replace('a','A')
   >> 'Abcde'
   a1.replace('a','')
   >> 'bcde'
   변환할 단어에 공백 입력시 제거도 가능하다. 
    ```
   
5. `split`
   1. 따옴표('') 기준으로 단어 분리
   ```
    a3='a;b;c'
    a3.split(';')     # a3에서 ';' 기준으로 분리한다.
    >> 'abc'
    a3.split(';')[1]  # 색인 가능
    >> 'b'
   ```
6. `대소치환`
   1. 문자를 대/소문자로 변경
   ```
    a1.upper()  # 대문자로 변경
   >> 'ABCDE'
   a1.lower     # 소문자로 변경
   >> 'abcde'
   ```
7. `find`
   1. 문자 찾기 함수
   ```
   a1.find('a')  # 'a'의 위치 출력
   >> 0
   a1.find('A')  # 없는 문자의 위치 출력하기
   >> -1
   ```
8. `count`
   1. 문자열에 해당 문자가 포함된 횟수 출력
   ```
   a1.conut(a)
   >> 1
   ```

# 연습 문제
```
ename='smith'
tel='02)345-7890'
jumin='901213-1234567'
vid='abc1234~!'
```
1. ename의 두번째 글자가 'm'으로 시작하는지 알아보자
<div style="color:white">ename[1]=='m'</div>
<div style="color:white">ename.startswith('m',2)</div>

2. tel에서 국번(345) 출력하기
<div style="color:white">방법1</div>
<div style="color:white">v1 = tel.find(')')</div>
<div style="color:white">v2 = tel.find('-')</div>
<div style="color:white">v1[v1+1:v2]</div>

<div style="color:white">방법2</div>
<div style="color:white">tel.split(')').split('-')[0]</div>

3. jumin에서 여자인지 확인하기
<div style="color:white">1) jumin.split('-')[1][1]=='2'</div>
<div style="color:white">2) jumin[7]=='2'</div>
<div style="color:white">3) jumin.startswith('2',7)</div>

