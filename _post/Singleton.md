---
title:"디자인 패턴 - 싱글톤"
date:2020-01-29
categories:Study
---
# 싱글톤

### 디자인 패턴(Design Pattern) 이란
디자인 패턴이란 프로그래밍 할 때에 특정 문맥에서 공통적으로 발생하는 문제를 해결하고자 코드의 구조들을 일정한 형태로 만들어 재이용하기 편리하게 만든 일정한 패턴. 

Singleton Pattern은 GoF(Gang of Four)가 정의한 패턴 중 하나  




### 의도
오직 한 개의 클래스 인스턴스만을 갖도록 보장하고, 이에 대한 전역적인 접근점을 제공합니다.  



### 활용성

단일체 패턴은 다음 상황에서 사용합니다.
-   클래스의 인스턴스가 오직 하나여야 함을 보장하고, 잘 정의된 접근점으로 모든 사용자가 접근할 수 있도록 해야 할 때
-   유일한 인스턴스가 서브클래싱으로 확장되어야 하며, 사용자는 코드의 수정 없이 확장된 서브클래스의 인스턴스를 사용할 수 있어야 할 때  


### 구조

![Singleton](https://scvgoe.github.io/img/singleton.gif)





### 간단 예제 코드

 - MySingleton.java

```java
    public class MySingleton {
    int kor = 10;
    
    private static MySingleton singleton = new MySingleton();
    public static MySingleton getInstance() {
        return singleton;
    }
```


 - MySingletonMain.java

```java
    public class MySingletonMain {
    
    public static void main(String[] args) {
    	//객체를 new 하더라도 매번 객체가 만들어지지 않도록 할 경우 싱글톤 패턴을 이용한다
    	//(Gof 디자인 패턴 중 하나)
		
		MySingleton s1 = new MySingleton();
		MySingleton s2 = new MySingleton();
		System.out.println(s1 + " " + s2);
		//아직까지는 주소가 다름, 따로 new 했기 때문
		
		s1.kor = 80;
		s2.kor = 100;
		System.out.println(s1.kor + " " + s2.kor);
		System.out.println();
		
		MySingleton s3 = MySingleton.getInstance();
		MySingleton s4 = MySingleton.getInstance();
		//new를 안하고 객체를 생성, 내부적으로 new를 이용해 객체를 생성했기 때문
		System.out.println(s3 + " " + s4); //주소가 같음 = 같은 오브젝트 참조
		
		s3.kor = 88;
		System.out.println(s3.kor + " " + s4.kor); 
		//같은 것을 참조하기 때문에 값이 같음
	}
}
```  




1. [GoF의 디자인 패턴 (Summary)](https://scvgoe.github.io/2018-12-24-GoF%EC%9D%98-%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-%28Summary%29-4.-%EB%8B%A8%EC%9D%BC%EC%B2%B4%28Singleton%29/)
2. [https://gone-sw.tistory.com/4](https://gone-sw.tistory.com/4)
3. [위키백과](https://ko.wikipedia.org/wiki/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EB%94%94%EC%9E%90%EC%9D%B8_%ED%8C%A8%ED%84%B4)
