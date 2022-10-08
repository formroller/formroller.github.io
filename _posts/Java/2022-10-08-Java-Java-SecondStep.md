---
layout : post
category: Java
title : "[2-1] 자바 시작하기"
tag :
- Java
- Basic
- structor
- type
- name
- comment
---
<font color='#98AFC7' size=3>자바에 대해 본격적으로 공부하기 전 반드시 알아두어야 할 가장 기본적인 것들에 대해 알아보자</font>

1.자바 소스코드의 구조
---
보통 일반적 자바 소스코드는 다음과 같은 형태로 만들어 진다.
```
/* 클래스 블록*/
public calss 클래스명{
    
    /*메소드 블록*/
    [public|private|protected] [static] (리턴자료형|void) 메소드명1 (입력자료형 매개변수,...){
        명령문(statement);
        ...
    }
    
    /*메소드 블록*/
    [public|private|protected] [static] (리턴자료형|void) 메소드명2 (입력자료형 매개변수,...){
        명령문(statement);
        ...
    }
    ...
}    
```
* class 블록
  - 소스코드의 가장 바깥쪽 영역
  - 클래스명은 소스파일명과 동일하게 사용해야 한다.
  - class 블록은 메소드 블록들을 포함한다.
* 메소드 블록  
  * [public]|[private]|[protected] - 접근 제어자
  * private > default > protected > public 순으로 많은 접근 허용한다.  
  
  **1.private**
     1. 접근 제어자가 private로 설정되었다면 private가 붙은 변수와 메소드는 **해당 클래스**에서만 접근 가능
     2. 아래 예제에서 secret변수와 getSercrete 메소드는 오직 Sample 클래스에서만 접근이 가능.
     ```
     public class Sample{
      pirvate String secret;
      private String getSecret(){  
              return this.secret;
      }
     }
  ```
  
  **2.Default**
  * 별도 접근 제어자 없는 경우 default가 접근 제어자가 되어 **해당 패키지 내**에서만 접근 가능  
  * 예시) house/HouseKim.java
    ```
    Package house;
    public class HouseKim{
      String lastname="kim"; // lastname은 dafault 접근 제어자로 설정.
    }
    ```
    
  * 예시) house/HousePark.java
  ```
  package house; //패키지 동일!
  public class HousePark{
    String lastname = "park";
    
    public static void main(String[] args){
      HouseKim kim = new HouseKim();
      System.out.println(kim.lastname); // HouseKim 클래스의 lastname 변수 사용 가능 
      }
  }
  ```
  * HouseKim과 HousePark의 패키지는 **house**로 동일.
  * -> HousePark클래스에서 HouseKim의 lastname 변수 접근 가능.  
  

  **3.Protected**
  * Protected가 붙은 변수, 메소드는 동일 패키지의 클래스 또는 해당 클래스를 상속받은 **다른 패키지의 클래스**에서만 접근 가능.
  * 예시) house/HousePark.java  

    ```
    *package house*; // 패키지 다름 
    public class HousePark{
      *protected* String lastname="Park";
    }
    ```
  * 예시) house/person/EunyoungPark.java
  ```
  package hose.person; // 서로 다른 패키지
  import house.HousePark;
  
    public class EunyoungnPark extends HousePark{ // HousePark을 상속.
        public static void main(String[] args){
          EunyoungPark eyp = new EunyoungPark();
          System.out.println(eyp.lastname); // 상속한 클래스의 protected 변수는 접근 가능.
        }
  }
  ```
  > 다른 패키지에도 사용 가능
  
  **4.public**
  * public 붙은 변수, 메소드는 어떤 클래스에서라도 접근 가능
  * 아래 예제의 HousePark의 info 변수는 public 접근 제어자가 붙어 있으므로 어떤 클래스라도 접근 가능.
  ```
  package house;
  public class HousePark{
      protected String lastname = "park";
      public String info = "this is public message."'
    }
  ```

2.변수의 자료형
---
* 변수명 규칙
  * 숫자로 시작할 수 없다.
  * _와 $ 이외 특수문자 사용 불가
  * 키워드는 변수명으로 사용 불가
  * 자료형 변수;로 구성
   ```
    int a;
    String b;
  
    a=1;
    b="hello java";
    ```
* 자주 쓰이는 자료형
  * int
    * 정수,4byte
  * long
    * 정수,8byte
  * double
    * 실수, 8byte (float, 4byte)
    * float보다 높은 정밀도가 필요할 경우 사용
  * boolean
    * true/false
  * char
    * 문자 타입(1개의 문자)
  * String
    * 문자열 타입
  * StringBuffer
    * String은 불변의 속성.
    * 자주 변경되는 자료의 경우 StringBuffer사용
  * List
    * 크기가 정해져 있지 않음.(배열과 차이점)
  * Map
    * key-value 자료
    * dictionary와 비슷
  * Set
    * 집합
    * 값들의 순서가 존재하지 않으며 중복되지 않음

3.명명 규칙
---
 1. 클래스명
    1. 클래스명은 명사로 한다.
    2. 여러 단어 섞이는 경우, 첫번째문자는 대문자(CalmelCase)
    ```
    (클래스명 예시)
    class Cookie{}
    class ChocoCookie{}
    ```
 2. 메소드명
    1. 메소드명은 동사로 지정.
    2. 첫문자는 소문자, 다음 문자는 대문자로 한다.
    ```
    (메소드명 예시)
    run();
    runFast();
    getBackground();
    ```
 3. 변수명
    1. 변수명은 짧지만 의미 포함(변수명을 통해 변수 사용 의도 파악 가능하게)
    2. 순서를 의미하는 임시의 정수 변수명은 i,j,k,m,n 사용(문자의 경우 c,d,e사용)
    3. 변수명에 **_**,**$** 기호 사용 가능하나 시작 문자로 사용하지 않음.
    ```
    (변수명 예시)
    int i;
    char c;
    float myWidth;
    ```
    
4.주석
---
1. 두 가지 주석
   1. 블록 주석
      ```
      /*
      프로그램의 저작권 
      
      이 프로그램의 저작권은 OOO에 있습니다.
      Copyright 2013.
      */
      public class MyProgram{
         ... 
      ```
    > 보통 블록 주석은 소스 코드내에서 한 블록(메소드, 클래스, 일정 부분)에 대한 설명시 주로 사용
   2. 라인 주석
      ```
      int age // 동물의 나이
      ```
   > 코드의 특정 부분에 대한 설명이 필요한 경우 사용