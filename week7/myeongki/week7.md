# 21장 소리치는 아키텍쳐
## 아키텍처의 테마
- 소프트웨어 아키텍처는 시스템의 유스케이스를 지원하는 구조
- 프레임워크는 사용하는 도구일 뿐, 아키텍처가 준수해야 할 대상이 아니다.
- 아키텍처를 프레임워크 중심으로 만들어버리면 유스케이스 중심이 되는 아키텍처는 절대 나올 수 없다.

## 아키텍처의 목적
- 좋은 아키텍처는 유스케이스에 중점을 두며, 지엽적인 관심사에 대한 결합은 분리시킨다.

## 하지만 웹은?
- 웹은 아키텍쳐일까? 시스템이 웹을 통해 전달된다는 사실이 시스템의 아키텍처에 영향을 주는가? 당연히 아니다. 웹은 전달 메커니즘이며, 애플리케이션 아키텍처에서도 그와 같이 다뤄야 한다.
- 애플리케이션이 웹을 통해 전달된다는 사실은 세부사항이며, 시스템 구조를 지배해서는 절대 안 된다.
- 시스템이 어떻게 전달될지에 대해 가능하다면 아무것도 몰라야 한다.

## 프레임워크는 도구일 뿐, 삶의 방식은 아니다.
- 프레임워크가 아키텍처의 중심을 차지하는 일을 막을 수 있는 전략을 개발하라.

## 테스트하기 쉬운 아키텍처
- 아키텍처가 유스케이스를 최우선으로 한다면, 그리고 프레임워크와는 적당한 거리를 둔다면 프레임워크를 전혀 준비하지 않더라도 필요한 유스케이스 전부에 대해 단위 테스트를 할 수 있어야 한다.

## 결론
- 아키텍처는 시스템을 이야기해야 하며, 시스템에 적용한 프레임워크에 대해 이야기해서는 안 된다.

# 22장 클린아키텍쳐

- 프레임워크 독립성
- 테스트 용이성
- ui 독립성
- 데이터 베이스 독립성
- 모든 에이전시에 대한 독립성

## 의존성 규칙
- 소스코드의 의존성은 반드시 안쪽으로 고수준의 정책을 향해야 한다.
- 외부 원에 위치한 어떤 것도 내부의 원에 영향을 주지 않기를 바란다.

## 엔티티
- 엔티티는 전사적인 핵심 업무 규칙을 캡슐화한다. 엔티티는 메서드를 가지는 객체이거나 일련의 데이터 구조와 함수의 집합일 수 있다. 기업의 다양한 애플리케이션에서 엔티티를 재사용할 수만 있다면, 그 형태는 그다지 중요하지 않다.

## 유스케이스
- 유스케이스 계층의 소프트웨어는 애플리케이션에 특화된 업무 규칙을 포함한다. 또한 유스케이스 계층의 소프트웨어는 시스템의 모든 유스케이스를 캡슐화하고 구현한다.
- 엔티티가 자신의 핵심 업무 규칙을 사용해서 유스케이스의 목적을 달성하도록 이끈다.


### 운영 관점에서 애플리케이션이 변경되는 것이 아니라면 서로 다른 계층의 변경에 의하여 변경이 이루어지는 계층을 뺀 나머지 계층에 영향을 주어서는 안된다.

## 인터페이스 어댑터
- 어댑터는 데이터를 유스케이스와 앤티티에게 가장 편리한 형식에서 데이터베이스나 웹 같은 외부 에이전시에게 가장 편리한 형식으로 변환한다.
- 프리젠터, 뷰, 컨트롤러는 모두 인터페이스 어댑터 계층에 속한다. 모델은 그저 데이터 구조 정도에 지나지 않으며, 컨트롤러에서 유스케이스로 전달되고 다시 유스케이스에서 프레젠터와 뷰로 되돌아 간다.
- 예로 sql 기반의 데이터베이스를 사용한다면 모든 sql은 이 계층을 벗어나서는 안 된다. 특히 이 계층에서도 데이터베이스를 담당하는 부분으로 제한되어야 한다.
- 또한 이 계층에는 데이터를 외부 서비스와 같은 외부적인 형식에서 유스케이스나 엔티티에서 사용되는 내부적인 형식으로 변환하는 또 다른 어댑터가 필요하다.

## 프레임워크와 드라이버
- 프레임워크와 드라이버 계층은 모든 세부사항이 위치하는 곳이다.

## 원은 네 개여야만 하나?
- 항상 네 개만 사용해야 한다는 규칙은 없다.
- 어떤 경우에도 의존성 규칙은 적용된다.
- 소스코드 의존성은 항상 안쪽을 향한다.
- 안쪽으로 향할수록 추상화와 정책의 수준은 높아진다.

## 경계 횡단하기
- 예로 컨트롤러 -> 유즈케이스 -> 프리젠터로 제어흐름이 발생한다고 가정하자 이때 의존성의 규칙을 깨지 않으려면 의존성 역전 원칙을 사용하여 해결할 수 있다.(인터페이스 사용)

## 경계를 횡단하는 데이터는 어떤 모습인가
- 경계를 가로지르는 데이터는 흔히 간단한 데이터 구조로 이루어져 있다.
- 데이터 구조가 어떤 의존성을 가져 의존성 규칙을 위배하게 되는 일은 바라지 않는다.
- 경계를 가로질러 데이터를 전달할 때, 데이터는 항상 내부의 원에서 사용하기에 가장 편리한 형태를 가져야만 한다.

## 결론
- 소프트웨어를 계층으로 분리하고 의존성 규칙을 준수한다면 본질적으로 테스트하기 쉬운 시스템을 만들게 될 것이다.

# 23장 프레젠터와 험블 객체
- 프레젠터는 험블 객체 패턴을 따른 형태로 아키텍처 경계를 식별하고 보호하는 데 도움이 된다.

## 험블 객체 패턴
- 험블 객체 패턴은 디자인 팬턴으로, 테스트하기 어려운 행위와 테스트하기 쉬운 행위를 단위 테스트 작성자가 분리하기 쉽게 하는 방법으로 고안되었다.
- 행위들을 두 개의 모듈 또는 클래스로 나눈다. 이들 모듈 중 하나가 험블이다. 가장 기본적인 본질을 남기고, 테스트하기 어려운 행위를 모두 험블 객체로 옮긴다. 나머지 모듈에는 험블 객체에 속하지 않은 테스트하기 쉬운 행위를 모두 옮긴다.
- 험블 객체 패턴을 사용하면 두 부류의 행위를 분리하여 프레젠터와 뷰라는 서로 다른 클레스로 만들 수 있다.

## 프레젠터와 뷰
- 뷰는 험블 객체이고 테스트하기 어렵다. 이 객체에 포함된 코드는 가능한 한 간단하게 유지한다. 뷰는 데이터를 gui로 이동시키지만, 데이터를 직접 처리하지는 않는다.
- 프레젠터는 테스트하기 쉬운 객체다. 프레젠터의 역할은 애플리케이션으로부터 데이터를 받아 화면에 표현할 수 있는 포멧으로 만드는 것이다. 이를 통해 뷰는 데이터를 화면으로 전달하기 간단한 일만 처리하도록 만든다.

## 데이터베이스 게이트웨이
- 유스케이스 인터렉터와 데이터베이스 사이에는 데이터베이스 게이트웨이가 위치한다. 이 게이트웨이는 다형적 인터페이스로, 애플리케이션이 데이터베이스에 수행하는 생성 조회 갱신 삭제 작업과 관련된 모든 메서드를 포함한다.
- 유스케이스는 sql을 호용하지 않고 유스케이스는 데이터베이스 게이트웨이를 물고 있는다. 그러므로 테스트하기 쉬운데, 이때 목 데이터베이스 게이트웨이를 주입해주는 것으로 테스트를 진행할 수 있기 때문이다.

## 데이터 매퍼
- 객체 관계 매퍼 같은 건 사실 존재하지 않는다.
- 객체는 데이터 구조가 아니기 때문이다. 최소한 객체를 사용하는 사람 관점에서 객체는 데이터 구조가 아니다. 데이터는 모두 private으로 선언되므로 객체의 사용자는 데이터를 볼 수 없다. 사용자는 객체에서 public 매서드만 볼 수 있다. 따라서 사용자 관점에서 볼 때 객체는 단순히 오퍼레이션의 결합이다.
- 객체와 달리 데이터 구조는 함축된 행위를 가지지 않는 public 데이터 변수의 집합이다. ->> 용어적 차이 결국은 converter를 어디에 위치 시킬까하는 이슈
- 게이트웨이 인터페이스와 데이터베이스 사이에서 일종의 또 다른 험블 객체 경계를 형성한다.

## 서비스 리스너
- 데이터를 애플리케이션에서 사용할 수 있게 간단한 데이터 구조로 포맷을 변경한다. 그런 후 이 데이터 구조는 서비스 경계를 가로질러서 내부로 전달된다.

## 결론
- 경계를 넘나드는 통신은 거의 모두 간단한 데이터 구조를 수반할 때가 ㄱ많고 대개 그 경계는테스트하기 어려운 무언가와 테스트하기 쉬운 무언가로 분리될 것이다. 그리고 이러한 아키텍처 경계에서 험블 객체 패턴을 사용하면 전채 시스템의 테스트 용이성을 크게 높일 수 있다.













