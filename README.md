# CocoaInternals

--

#

## 

1. 프로그래밍 패러다임에는 크게 두 가지 축이 있습니다. 하나는 앨런 튜링이 제안한 튜링 머신에 적합한 프로그래밍 방식이고, 또 다른 하나는 알론조 처치가 제안한 람다 계산식을 구현하는 프로그래밍 방식입니다.
2. 객체중심에 대한 개념은 서양철학의 줄기를 따라가 보면 개개인을 중심으로 자연의 모든 것을 관찰하고 분류하고 부석했던 아리스토텔레스의 자연철학에서부터 비롯됐다는 것을 알 수 있다.
3. 객체라는 단어는 주체(나)를 중심으로 하는 1인칭 시점에서 바라볼 때 세상의 모든 것을 지칭하는 단어다.
4. 오브젝티브-C에 붙어있는 형용사 오브젝티브는 의미 그대로 객관적으로 객체를 바라보고 추상화시켜 표현하기 위한 언어라는 것을 의미한다.
5. 실생활의 객체들을 책임과 역할에 따라 구분하고 객체 사이의 관계와 연결하도록 생각하는 방식은 객체 중심 프로그래밍 패러다임을 이루는 골격이다.
6. 스위스 언어학자 소쉬르는 같은 언어를 사용하는 사람들끼리 생각하는 방식에 대한 원칙(단어의 의미, 문법)을 랑그라고 하고 , 실제 대화나 상황에 따라서 표현이나 발음이 달라지는 것을 파롤이라고 했다. 이런 일반적인 언어에서 랑그와 파롤의 개념은 프로그래밍 언어에서도 그대로 존재한다.
7. 브래드 콕스는 소프트웨어도 하드웨어와 마찬가지로 공장에서 생산하는 부품처럼 부품화해야한다고 생각했다.
8. 스위프트에서 클래스 타입은 오브젝티브-C와 호환성을 유지하는 객체로 쓸 수도 있고, 호환이 되지 않는 네이티브 객체(native object)로 사용할 수도 있다.
9. 객체 인스턴스는 각각 고유한 메모리 영역을 차지하기 때문에, 동일한 속성(혹은 변수)에 대해서도 각자의 메모리 영역에 데이터를 보관한다.
10. 동일한 객체가 아니지만 각 메모리에 저장하고 있는 값이 동일하다면 객체속성에 대한 등가성을 갖는다고 한다.
11. 등가성을 비교할 떄는 == 비교문은 성립되지 않는다.
12. 모든 코코아 객체 인스턴스가 힙영역에 생성되는 것은 아니다. 특이하게 힙 영역이 아닐 ㅏ텍스트 영역과 데이터 영역에 생기는 경우가 있다.
13. NSString 클래스는 NSObject에서 상속받는 코코아 클래스 중에서 유일하게 전역변수로 선언할 수 있다.
14. 스위프트에서 String 객체는 네이티브 문자열 객체를 만들 수도 있고 NSString을 연결해서 쓸 수도 있다.
15. 네이티브 문자열 객체는 내부적으로 인터닝을 시키는 NSString 객체와는 다르게 텍스트 영역에 있는 문자열을 OpaquePointer향태 포인터로 그대로 연결하는 방식을 사용한다. 따라서 네이티브 문자열이 NSString 객체보다는 좀 더 가벼운 형태라고 할 수 있다.
16. 스위프트에서는 객체뿐만 아니라 모든 타입에 Hashable 프로토콜을 구현해야한다.
17. 클래스와 메타 클래스를 메모리에 로딩하는 역할은 오브젝티브-C 런타임이 담당한다. 런타임은 실행 중에 객체에게 보내는 메시지를 처리할 메서드를 찾거나 객체 메모리 관리, 동적 타입 벼환 등을 처리하는 C 함수 라이브러리다.
18. 오브젝티브-C는 객체의 메서드를 직접 호출하지 않고 스몰토크 언어에서처럼 객체에 메시지를 보내는 방식으로 동작한다.
19. 찾은 메모리 주소는 한 번만 쓰고 버리는 것이 아니라 내부 캐시에 저장하고 이후에는 캐시에어 먼저 찾는다.
20. 메서드 선택방법을 최적화하기 위해서 메서드에 대한 구현부 메모리 주소를 시스템 수준의 캐시로 저장한다.
21. 메시지를 처리할 메서드를 찾을 때마다 해시 값으로 캐시를 확인하고 데이터가 없거나 메모리 주소가 바뀌면 새로 업데이트 한다.
22. 오브젝티브-C 런타임이 제공하는 API와 실행 중에 객체와 메서드 블록 같은 어어 기능등을 처리하는 방식을 알아두면 내부 동작을 이해하는 데 도움이 된다.
23. 오브젝티브-C가 가지는 장점들은 모두 런타임에서 발현된다.
24. 특히 런타임 API를 사용하면 실행 중에 클래스나 객체의 구조나 함수를 바꾸는 동작이 가능하다. 다른 프로그래밍 언어에서는 이를 리플렉션(reflection)이라고 부른다.

---

#

## 2장 메모리 관리

1. 모든 객체 인스턴스는 메모리에 만들어진다. 그중에서도 객체에 대한 메모리 관리는 필수적이다. 효율적으로 메모리를 관리하는 것은 macOS나 iOS 구별할 것 없이 성능에 영향을 주는 아주 중요한 사항이다.
2. 운영체제가 관리하는 프로세스는 이론적을 32bitㅇ



