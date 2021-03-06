# 추상 팩토리(Abstract Factory) - 객체 생성(Object Creational)

* 의도 : 상세화된 서브클래스를 제공하지 않고도, 서로 관련성이 있거나 독립적인 여러 객체의 군을 생성하기 위한 인터페이스를 제공합니다.
* 다른 이름 : 키트(Kit)
* 동기 : 응용프로그램이 플랫폼 독립적인 인터페이스를 이용하도록 하여 이식성을 가지게 하기 위해서
* 활용성 
	1. 객체의 생성, 구성, 표현 방식과 무관하게 시스템을 독립적으로 만들고자 할 때
	2. 여러 제품군 중 하나를 선택해서 시스템을 설정해야 하고, 한번 구성한 제품을 다른 것으로 결정해야 할 때
	3. 관련된 제품 객체들이 함께 사용되도록 설계되었고, 이 부분에 대한 제약이 외부에도 지켜지도록 하고 싶을 때
* 구조  
	![abstractFactory](/img/AbstractFactory.JPG)
* 참여자
	* AbstractFactory : 개념적 제품에 대한 객체를 생성하는 연산, Client가 쓸 인터페이스를 정의한다.
	* ConcreteFactory : 구체적인 제품에 대한 객체를 생성하는  연산을 구현합니다.  
	* AbstractProduct : 개념적 제품 객체에 대한 인터페이스를 정의한다. 이 인터페이스를 Client가 사용한다.
	* ConcreteProduct : 구체적으로 팩토리가 생성할 객체를 정의하고, AbstractProduct가 정의하는 인터페이스를 구현한다.
	* Client: AbstractFactory와 AbstractProduct의 인터페이스를 사용하는 대상.
* 협력 방법 
	* ConcreteFactory 클래스의 인스턴스 한 개가 런타임에 생성되고, 이 Factory 인스턴스를 통해 실 사용할 제품 객체를 만들어낸다. 다른 제품 객체를 만들려면 다른 ConcreteFactory가 필요하다.
	* AbstractFactory는 필요한 제품 객체를 생성하는 책임을 ConcreteFactory 서브 클래스에 위임한다.  
* 결과
	1. 구체적인 클래스를 분리한다. 
	2. 제품군을 쉽게 대체할 수 있도록 한다.
	3. 제품 사이의 일관성을 증진시킬 수 있다.
	4. 새로운 종류의 제품을 제공하기는 어렵다. -> Abstract Factory의 변경은 ConcreteFactory 전체의 변경을 불러온다.
* 구현
	1. 팩토리를 단일체로 정의한다. -> 한 제품군에 대해, 하나의 Factory만 있으면 되기 때문이다.
	2. 제품을 생성한다.
		* Product별로 ConcreteFactory를 만든다.
		* 원형 패턴을 이용해서, 원하는 타입의 인스턴스를 넘겨줌으로써 ConcreteFactory의 수를 줄일 수 있다.
	3. 확장 가능한 팩토리를 정의한다.
		* 유연한 인터페이스 <-> 확장 가능한 인터페이스
* 관련 패턴
	* 팩토리 메서드 패턴
	* 원형 패턴
	* 단일체 패턴