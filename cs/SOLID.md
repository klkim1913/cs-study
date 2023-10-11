# 객체 지향 설계의 5원칙 S.O.L.I.D

- 좋은 소프트웨어? 변화에 대응을 잘 하는 것
- 좋은 설계: 시스템에 새로운 요구사항이나 변경사항이 있을 때, 영향을 받는 범위가 적은 구조 -> 시스템에 예상하지 못한 변경사항 발생시, 유연하게 대처하고 이후에 확장성이 있는 시스템 구조를 만들 수 있음.

- SOLID 객체 지향 원칙을 적용하면 **코드를 확장**하고 **유지 보수 관리**하기가 더 쉬워지며, 불필요한 **복잡성을 제거**해 리팩토링에 소요되는 시간을 줄임으로써 프로젝트 **개발의 생산성**을 높일 수 있다.

## 단일 책임 원칙 - SRP(Single Responsibility Principle)

- 클래스(객체)는 단 하나의 책임만 가져야 한다.
    * 한 책임의 변경으로부터 다른 책임의 변경으로의 연쇄작용 방지
- 책임 = 기능 담당

> 프로그램의 유지보수성을 높이기 위한 설계 기법

## 개방 폐쇄 원칙 - OCP(Open Closed Principle)

- 확장에 열려있어야 하며, 수정에는 닫혀있어야 한다.
- 기능 추가 요청이 오면 클래스를 확장을 통해 손쉽게 구현하면서, 확장에 따른 클래스 수정은 최소화.
- 추상화 사용을 통한 관계 구축을 권장

> 다형성과 확장을 통해 객체지향의 장점을 극대화하는 설계 원칙

## 리스코프 치환 원칙 - LSP(Liskov Substitution Principle)

- 서브 타입은 언제나 부모 타입으로 교체할 수 있어야 한다.
- 다형성 원리를 이용하기 위한 원칙
- 업캐스팅된 상태에서 부모의 메서드를 사용해도 동작이 의도대로 흘러가야 하는 것

```java
public void myData() {
	// Collection 인터페이스 타입으로 변수 선언
    Collection data = new LinkedList();
    data = new HashSet(); // 중간에 전혀 다른 자료형 클래스를 할당해도 호환됨
    
    modify(data); // 메소드 실행
}

public void modify(Collection data){
    list.add(1); // 인터페이스 구현 구조가 잘 잡혀있기 때문에 add 메소드 동작이 각기 자료형에 맞게 보장됨
    // ...
}
```

- LSP원칙의 핵심은 상속 -> 상속은 기반 클래스와 서브 클래스 사이에 IS-A관계가 있을 경우로만 제한되어야 한다. -> 그 외의 경우에는 합성 이용

> 내가 자바를 만들면서 가장 후회하는 일은 상속을 만든 점이다 - Java의 창시자 -
> 상속읠 위한 설계와 문서를 갖추거나, 그럴 수 없다면 상속을 금지하라. - Effective Java -

## 인터페이스 분리 원칙 - ISP(Interface Segregation Principlr)

- 인터페이스를 각각 사용에 맞게 잘게 분리해야 한다.
- SRP은 클래스의 단일 책임, ISP는 인터페이스의 단일 책임
- 클라이언트의 목적과 용도에 적합한 인터페이스 만을 제공
- 한번 인터페이스를 분리하여 구성해놓고 나중에 무언가 수정사항이 생겨서 또 인터페이스들을 분리하면 안됨.

## 의존 역전 원칙 - DIP(Dependency Inversion Principle)

- 어떤 클래스를 참조해서 사용해야 한다면, 직접 참조가 아닌 그 대상의 상위 요소로 참조하라는 원칙
-> 인터페이스에 의존하라
- 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것보다는, 변화하기 어려운 것에 의존하라는 것.
> 의존 역전 원칙의 지향점은 각 클래스간의 결합도를 낮추는 것.