---
layout : post
category : Java
title : "[1-2] 안녕 세상!(Hell World!)"
---
1.Java 설치하기(MAC)
---
 1.1 [Homebrew](https://brew.sh/index_ko) 설치 및 업데이터
  ```
   brew update
  ```
  1.2 adoptopenjdk/openjdk 추가하기 
 ```
 brew tap adoptopenjdk/openjdk
 ```
  1.3 설치 가능한 모든 JDK 찾기
  ```
  brew search jdk
  ```
  1.4 원하는 버전 설치
  ```
  brew install --cask adotopenjdk11
  brew install --cask adotopenjdk[nn] * nn, 설치 버전
  ```
  1.5 버전 확인 
  ```
  java --version
  ```

2.JDK란 
---
 * JDK는 **Java Development Kit**의 약자로 Java로 소프트웨어를 개발할 수 있도록 여러 기능을 제공하는 패키지(키트)라 한다.
 * JDK 종류
   1. Java SE
      1. 표준 자바 플랫폼
      2. 표준적인 컴퓨팅 환경을 지원하기 위한 자바 가상머신 규격 및 API 집합을 포함
   2. Java EE
      1. Java SE에 웹 어플리케이션 서버에서 동작하는 기능을 추가하는 플랫폼
      2. 이 스펙에 따라 제품을 구현한 것을 웹 어플리케이션 서버(WAS)라 한다.(ex-tomcat)
      > [WAS와 웹 서버의 차이점](http://sungbine.github.io/tech/post/2015/02/15/tomcat과%20apache의%20연동.html)
   3. Java ME
      1. 제한된 자원을 가진 휴대전화, PDA 등에서 Java 프로그밍 언어를 지원하기 위해 만든 플랫폼 중 하나이다.

3.Hello World! 출력하기  
---
 - 메소드(method)는 함수(function)와 동일한 개념이다. HelloWorld 클래스를 실행하려면 main 메소드를 작성해야 한다. 
 - 어떤 프로그램이라도 시작과 끝이 존재하며, 이를 관리하는 것이 **main**메소드이다. 
   > 메소드(method)는 함수(function)와 동일한 개념이다.
   > 다만 클래스 내의 함수는 보통 메소드라 하며, 자바는 모든 것이 클래스 기반이므로 자바에서 사용되는 함수는 모두 메소드이다.   
 
```
public class HelloWorld{
   public static void main(String[] args){
      System.out.println("Hello World");
   }
}    
```
main 메소드에 알 수 없는 public, static, void, String[], args, System.out.println에 대해 알아보자.

 * public
   * 메소드의 접근 제어자
   * public은 누구나 해당 메소드에 접근할 수 있다는 의미
 * static
   * 메소드에 static 지정된 경우 인스턴스 생성없이 실행 가능
 * void
   * 메소드의 리턴값 없음을 의미
 * String[] 
   * 문자열을 나타내는 자바의 자료형 (**[]**는 배열을 의미)
 * args 
   * String[] 자료형에 대한 변수명
 * System.out.println()
   * 문자열을 화면에 출력(자바 내장 메소드)