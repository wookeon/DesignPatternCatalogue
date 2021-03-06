# 적응자(Adapter) - 클래스, 객체구조 

* 의도 : 클래스의 인터페이스를 사용자가 기대하는 인터페이스로 적응(변환) 시킨다.
* 동기 : 이미 존재하는 클래스의 인터페이스가 맞지 않을 때 이를 맞추고 싶다.
* 활용성
	* 기존 클래스를 쓰려는데 인터페이스가 맞지않다.
	* 재사용하려는 라이브러리의 수정이 불가능하다.
	* (객체 적응자만 해당) 이미 존재하는 여러 서브클래스들을 써야하는데, 이 서브클래스를 상속받아 인터페이스를 모두 개조하는 것이 현실성이 없을 때
* 구조
  * 클래스 적응자
    ![classAdapter](/img/classAdapter.JPG)
  * 객체 적응자
    ![objectAdapter](/img/objectAdapter.JPG)
* 참여자
	* Target : 응용 분야에 종속적인 인터페이스를 정의하는 클래스
	* Client : Target 인터페이스를 만족하는 객체와 동작할 대상
	* Adaptee : Adapter를 통해 인터페이스를 적응시켜야 하는 대상
	* Adapter : Target 인터페이스에 Adaptee를 적응시키는 클래스
* 협력 방법 : 적응자에 해당하는 클래스의 인스턴스에게 연산을 호출하고, 적응자는 해당 요청을 수행하기 위해 적응대상자의 연산을 호출한다.
* 결과
	* 클래스 적응자
		* Adapter 클래스가 Adaptee 클래스를 상속 받아 Target 인터페이스를 맞추는데, 서브클래스들이 너무 많다면 적용하는 것이 어렵다.
		* Adaptee를 상속받기 때문에, Adaptee에 정의된 행동들을 재정의할 수 있다.
		* Adaptee를 접근하기 위한 추가 포인터 간접화는 필요없다.
	* 객체 적응자
		* 하나의 Adpater 클래스로 Adaptee의 모든 서브클래스들에 접근할 수 있다.
		* Adaptee 클래스의 행동을 재정의하는 것은 매우 어렵다.
	* 고려사항
		* Adapter 클래스가 실제 적응 작업을 위해 들어가는 품이 얼마나 되나? -> Target과  Adaptee의 유사성이 크면 
		* 대체 가능(Pluggable) 적응자 -> Adaptee 클래스를 정의할 때, 누가 사용할 것인지에 대한 생각을 최소화해서 재사용성을 높이고, 적응자를 바꿈으로써 실제 시스템에 적용한다.
		* 양방향 적응자(two-way adapter) -> 개조되는 두 클래스의 인터페이스를 모두 상속받아 정의하는 것
* 구현
	* C++로 클래스 적응자 구현시 -> Adapter는 Target을 public, Adaptee를  private로 상속 받아야 한다.  -> Adapter는 Target의 서브 클래스지만, Adaptee의 서브 클래스는 아니게 된다.
	* 대체 가능 적용자
		* 공통 : 적응이 필요한 연산의 최소집합을 정의한다.
		* 방법 1 : 추상 연산을 사용하는 방법
		* 방법 2 : 위임 객체를 사용하는 방법
		* 방법 3 : 매개변수화 된 적응자를 사용하는 방법
* 관련 패턴
	* 가교 패턴 : 유사하나 목적이 다름(구현과 추상 개념을 분리해 각자 확장하도록 하려는 것)
	* 장식자 패턴 : 다른 인터페이스의 변경 없이 새로운 행동을 추가할 수 있도록 한다.  -> 순수한 적응자로는 불가능한 재귀적 합성을 가능하게 함
	* 프록시 패턴 : 다른 객체에 대한 대표자 또는 대리인 역할 수행 -> 인터페이스를 변경하는 책임은 없다.