---
layout : post
category : Java
title : "[1-3] 자바 산책하기"
tag:
 - Java
 - class
 - main
 - variable
 - method
 - object
 - for
 - gugudan
 - multiple
---
1.클래스 생성
---
 - 인텔리제이 구동을 통해 GuGu 클래스 생성하자
*GuGu.java*
```
public class GuGu{
}
```

2.변수
---
1. main 메소드에 숫자형 변수 생성 
```
public class GuGu{
    public static void main(String[] args){
        int n;
    }
}    
```
2. 변수에 값 대입
```
public class GuGu{
    public static void main(String[] args){
        int n;
        n = 4; // 가능
        n = "123"; // 컴파일 오류 - 타입 오류
    }
}    
```
3. 2단 생성(구구단)
```
public class GuGu{
    public static void main(String[] args){
        int n = 2;
        
        System.out.println(n*1);
        System.out.println(n*2);
        System.out.println(n*3);
        System.out.println(n*4);
        System.out.println(n*5);
        System.out.println(n*6);
        System.out.println(n*7);
        System.out.println(n*8);
        System.out.println(n*9);
    }
}    
```
이제 구구단 중 2단 출력이 가능하게 되었다.


3.메소드
---
**2단부터 9단까지 모두 한번에 보고싶다면?**  
 이 문제를 해결하기 위해 한 개의 숫자를 입력받아 그 숫자에 대한 구구단을 출력하는 메소드 생성  
(다음은 dan 메소드가 추가된 GuGu 클래스이다.)

```
public class GuGu{
    public void dan(int n){
        System.out.println(n*1);
        System.out.println(n*2);
        System.out.println(n*3);
        System.out.println(n*4);
        System.out.println(n*5);
        System.out.println(n*6);
        System.out.println(n*7);
        System.out.println(n*8);
        System.out.println(n*9);
 }
    public static void main(String[] args){
        int n = 3;
  }
}  
```
 - main 메소드에 구현한 내용이 dan 메소드에 옮겨져있다.
 - dan 메소드는 입력으로 정수값(n)을 입력받아 1-9까지 곱한 값을 출력하는 메소드이다.
 - 메소드의 가장 중요한 부분은 **입력/출력**이다.
   - 입력 : 정수 자료형 1개(int n)
   - 출력 : 없음(void)

 - 메도스는 이러한 입출력을 반드시 선언해야 한다. 위 출력값에 의해 dan 메소드는 아래와 같이 구현되어있다.
```
public void dan(int n){
    (...생략...)
}    
```
 - public은 해당 메소드에 접근할 수 있는 접근제어자이다.
 - public으로 선언시 이 메소드는 어떤 곳에서든지 호출 가능 

4.객체
---
 - dan 메소드 호출하기
   - GuGu 클래스는 반드시 main 메소드부터 시작하므로, main 메소드에서 dan 메소드를 호출해야 한다.
 - GuGu 클래스의 dan 메소드 호출위해서는 GuGu 클래스의 객체를 생성한 후 생성된 객체를 통해 dan 메소드를 호출해야 한다.
```
(...생략...)
    public static void main(String[] args){
        int n = 3;
        GuGu gugu = new GuGu(); // GuGu 클래스의 객체 생성
        gugu.dan(n); // 객체를 통해 dan 메소드 호출
    }
(...생략...)   
```
GuGu 클래스의 객체를 만드는 방법은 다음과 같다
```
GuGu gugu = new GuGu();
```
**int n**에서 n이 int 자료형임을 알 수 있듯, 위 예의 **GuGu gugu** 문장은 gugu가 GuGu 클래스의 자료형임을 나타낸다.   
따라서 gugu변수에서는 GuGu 클래스로 생성한 객체만 대입 가능하다.

 - GuGu 클래스의 객체를 만들기 위해서는 **new** 키워드를 사용한다.
```
GuGu gugu = new GuGu();
```
 - 이처럼 gugu객체를 생성하면 gugu 객체를 통해 GuGu 클래스의 dan 메소드를 사용할 수 있다. 
 - 객체를 통해 클래스의 메소드에 접근하기 위해서는 도트 연산자를(.) 이용한다.
```
gugu.dan(n);
```
 - gugu 객체를 통해 dan 호출로 2부터 9단까지 출력하기 
```
public class GuGu{
    public void dan(int n){
        System.out.println(n*1);
        System.out.println(n*2);
        System.out.println(n*3);
        System.out.println(n*4);
        System.out.println(n*5);
        System.out.println(n*6);
        System.out.println(n*7);
        System.out.println(n*8);
        System.out.println(n*9);
    }    
       
    public static void main(String[] args){
        GuGu gugu = new GuGu();
        gugu.dan(2);
        gugu.dan(3);
        gugu.dan(4);
        gugu.dan(5);
        gugu.dan(6);
        gugu.dan(7);
        gugu.dan(8);
        gugu.dan(9);
    }
}        
```

## 👉🏻 static 메소드
 GuGu 클래스의 dan 메소드를 호출하려면 GuGu 클래스의 객체를 먼저 생성한 후, 그 객체의 메소드인 dan 메소드를 호출해야 한다.   
 하지만 dan 메소드를 main 메소드처럼 static으로 선언한다면 다음과 같이 객체 생성없이 메소드 호출만으로 가능하다.
```
public class GuGu{
    public *static* void dan(int n){
        (...생략...)
    }
    
    public static void main(String[] args){
        *dan(2)*;
    }
}    
```

5.for문
---
1. 입력으로 받은 숫자인 n에 1부터 9까지 곱해 출력하는 문장이 반복된다. 
```
public class GuGu{
    public void dan(int n){
        for (int i=1; i<10; i++){  // i에 1-9까지 값이 반복해 대입된다. 
            System.out.println(n*i);
        }
    }
    public static void main(String[] args){
        GuGu gugu = new GuGu();
        gugu.dan(2);
        gugu.dan(3);
        gugu.dan(4);
        gugu.dan(5);
        gugu.dan(6);
        gugu.dan(7);
        gugu.dan(8);
        gugu.dan(9);
    }
}            
```
2. main 메소드에 for문 적용 
```
public class GuGu{
    public void dan(int n){
        for (int i=1;i<10;i++);
        }
    }
    
    public static void main(String[] args){
        GuGu gugu = new GuGu();
        for (int i=2; i<10; i++){ // i에 2-9까지 값이 반복 대입된다. 
            gugu.dan(i)
        }    
    }
}    
```

6.구구단 만들기
---
GuGu.java
```
public class GuGu{
    public void dan(int n){
        for (int i=1;i<10;i++){
            System.out.println(n*i);
        }
    }
    public static void main(String[] args){
        GuGu gugu = new GuGu();
        for (int i = 2; i<10; i++){
            gugu.dan(i);
        }
    }
}    
```