---
layout: post 
category: Java 
title: "[3-1] 숫자, 불리언, 문자"
tag:
- Java
- Basic
- Type
- Number
- boolean
- char 

use_math: true 
comments: true
---

<font color="##778899" size="3">그 언어의 자료형을 알게 된다면 이미 그 언어의 반을 터득한 것이나 다름없다.</font>

1.숫자형(Number)
---

1. 정수
    1. 정수를 표현하기 위한 자료형은 int, long이다.
    2. int와 long 차이 표현할 수 있는 숫자 범위

   |**자료형**|**표현범위**|
      |---|---|
   |int|-2147483648 ~ 2147483648|
   |long|-9223372036854775808 ~ 9223372036854775808|

   > long 변수에 2147483647보다 큰 값 대입시 문자 끝에 "L" 덧붙여야 한다.
   
2. 실수
    1. 실수를 표현하기 위한 자료형은 float와 double이다.
    2. float와 double 차이 표현할 수 있는 숫자 범위
       
   |**자료형**|**표현범위**|
   |--|--|
   |float|$\pm3.4*10^{38}$|
   |double|$\pm1.7*10^{308}$|

3. 8진수와 16진수
   1. int 자료형을 사용해 표시한다.
   2. 0(숫자 0)으로 시작하면 8진수, 0x로 시작하면 16진수가 된다.
   ```
   int octal = 023;  // 십진수 : 19
   int hex = 0xC;  // 십진수 : 12
   ```
   
4. 숫자연산(+,-,*,/)
   ```
   (사칙연산 예시)
   public class Sample{
      public static void main(String[] args){
         int a=10;
         int b=5;
         System.out.println(a+b);
         System.out.println(a-b);
         System.out.println(a*b);
         System.out.println(a/b);
         System.out.println(a%b);  //나머지 출력
      }
   }
   
   >> 15
   >> 5
   >> 50
   >> 2
   >> 0
   ```

5. 증감연산(++,--)
   1. **i++** : 값이 참조된 후 증가
   2. **++i** : 값이 참조되기 전 증가

> [참고 - 깃블로그 수식 넣기](https://mkkim85.github.io/blog-apply-mathjax-to-jekyll-and-github-pages)