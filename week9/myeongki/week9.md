# 27장 크고 작은 모든 서비스들
## 서비스 지향 아키텍처와 마이크로서비스 아키텍처는 최근에 인기를 끌고 있다. 그 이유는
- 서비스를 사용하면 상호 결합이 철저하게 분리되는 것처럼 보인다. 일부만 맞는 말.
- 서비스를 사용하면 개발과 베포 독립성을 지원하는 것처럼 보인다. 이 역시도 일부만 맞는 말.

## 서비스 아키텍처?
- 프로세스나 플랫폼 경계를 가로지르는 함수 호출에 지나지 않는다.
- 단순히 애플리케이션의 행위를 분리할 뿐인 서비스라면 값비싼 함수 호출에 불과하며, 아키텍처 관점에서 꼭 중요하다고 볼 수는 없다.
- 서비스 그 자체로 아키텍처를 정의하지 않는다.
- 서비스는 프로세스나 플랫폼 경계를 가로지르는 함수 호출에 지나지 않는다.

## 서비스의 이점?
### 결함 분리의 오류
- 시스템을 서비스들로 분리함으로써 얻게 되리라 예상되는 큰 이점 하나는 서비스 사이의 결합이 확실히 분리된다는 점이다.
- 서비스는 다른 서비스의 변수에 직접 접근할 수 없다.
- 인터페이스는 반드시 잘 정의 되어 있어야 한다.
- 이 말에는 어느정도 일리가 있지만, 꼭 그런 것만은 아니다. -> 네트워크 연결 or 디비로 강하게 연결 가능성이 존재한다.
- 서비스 인터페이스가 함수 인터페이스보다 더 엄밀하거나, 더 엄격하고 , 더 잘 정의 되는 것은 아니다. 이러한 이점은 환상이다..

### 개발 및 배포 독립성의 오류
- 서비스 아키텍처를 통하여 얻은 개발 및 배포 독립성을 확장 가능한 것으로 간주된다.
- 극히 일부.. -> 대규모 엔터프라이즈 시스템은 서비스 기반 시스템 외에도 모노리틱 시스템이나 컴포넌트 기반 시스템으로도 구축할 수 있다는 사실은 역사적으로 증명되어 왔다. -> 유일한 선택지가 아니다.
- 서비스라고 해서 항상 독립적으로 개발하고 배포하며 운영할 수 있는 것은 아니다.결합된 정도에 맞게 개발 배포 운영을 조정해야만 한다.

## 야옹이 문제
- 기존 서비스에 아예 새로운 기능이 추가되는 경우에 서비스 아키텍처라 하더라도 모든 부분을 수정해야한다. -> 야옹이 서비스를 추가하는 예..

## 객체가 구출하다
- 원래 서비스의 로직 중 대다수가 이 객체 모델의 기반 클레스 내부로 녹아들었고 배차에 특화된 로직 부분은 rides 컴포넌트로 추출되고 야옹이에 대한 신규 기능은 kittens 컴포넌트에 들어갔다.
- 컴포넌트 팩토리를 통하여 각 컴포넌트(라이드, 야용이)에서 적절한 클레스를 배치하여 해결할 수 있다.

## 단일 컴포넌트 기반 서비스
- 서비스가 반드시 소규모 단일체여야 할 이유는 없다.

## 횡단 관심사
- 모든 주요 시스템이 직면하는 횡단 관심사를 처리하려면 서비스 내부 의존성 규칙도 준수하는 컴포넌트 아키텍처로 설계해야 한다. 이 서비스들은 시스템의 아키텍처 경계를 정의하지 않는다. -> 아키텍처 경계를 정의하는 것은 서비스 내에 위치한 컴포넌트다.


## 결론
- 서비스는 시스템의 확장성과 개발 가능성 측면에서 유용하지만, 그 자체로는 아키텍처적으로 그리 중요한 요소는 아니다.
- 서비스는 단 하나의 아키텍처 경계로 둘러싸인 단일 컴포넌트로 만들 수 있다. 혹은 여러 아키텍처 경계로 분리된 다수의 컴포넌트로 구성할 수도 있다.

# 28장 테스트 경계

## 시스템 컴포넌트인 테스트
- 아키텍처 관점에서는 모든 테스트가 동일하다.
- 테스트는 시스템 컴포넌트 중에서 가장 고립되어 있다.
- 깨지기 쉬운 테스트는 시스템을 뻣뻣하게 만든다는 부작용을 낳을 때가 많다.
- 설계할 때 gui를 사용하지 않고 업무 규칙을 테스트할 수 있게 해야 한다.

## 테스트 api
- 테스트 api는 테스트를 애플리케이션으로부터 분리할 목적으로 사용한다. 단순히 테스트를 ui에서 분리하는 것만이 아닌, 테스트 구조를 애플리케이션 구조로부터 결합을 분리하는게 목표다.
- 구조적 결합이 강하면 필수적인 진화 과정을 방해할 뿐만 아니라, 사용 코드의 범용성과 유연성이 충분히 좋아지지 못하게 막는다.

## 결론
- 시스템의 일부로 봐야지 테스트 코드가 버려지지 않는다.

# 29장 클린 임베디드 아키텍처

- 소프트웨어는 닳지 않지만, 펌웨어와 하드웨어는 낡아 가므로 결국 소프트웨어도 수정해야 한다.
- 하드웨어는 발전할 수밖에 없고 그러한 현실을 염두에 두고 임베디드 코드를 구조화 할 수 있어야 한다.
- 임베디드 엔지니어가 아닌 당신도 코드에 sql을 심어 놓거나 개발하는 코드 전반에 플랫폼 의존성을 퍼뜨려 놓는다면, 본질적으로 펌웨어를 작성한 셈이다.

## 앱 티튜드 테스트
-임베디드 코드가 동작하게 만드는 데 대부분의 노력을 집중하고, 오랫동안 유용하게 남도록 구조화하는 데는 그리 신경을 쓰지 않기 때문으로 보인다.

- 먼저 동작하게 만들어라
- 올바르게 만들어라 -> 코드를 리팩터링해서 당신을 포함한 나머지 사람들이 이해할 수 있게 만들고, 요구가 변경되거나 요구를 더 잘 이해하게 되었을 때 코드를 개선할 수 있게 만들어라.
- 그리고 빠르게 만들어라. 코드릴 리팩토링해서 요구되는 성능을 만족 시켜라

## 타깃 하드웨어 병목현상
- 코드를 테스트할 수 있는 환경이 해당 특정 타깃으로 국한될 것이다 그리고 그 타깃이 테스트가 가능한 유일한 장소라면 타깃 하드웨어 병목현상이 발생하여 진척이 느려질 것이다.

## 클린 임베디드 아키텍처는 테스트하기 쉬운 임베디드 아키텍처다.
- 몇가지 아키텍처 원칙을 임베디드 소프트웨어와 펌웨어에 적용하여 타깃 하드웨어 병목현상을 줄이는 방법을 살펴보다.


## 계층
- 하드웨어, 펌웨어, 소프트웨어 이렇게 3개의 계층으로 나누어 생각해 보자
- 펌웨어와 소프트웨어를 계층을 분리하지 않고 막 작성하면 하드웨어, 펌웨어로 계층이 2가지로 나뉘게 된다.
- 이런 경우 소프트웨어와 펌웨어가 서로 섞이는 일은 안티 패턴이다. -> 변경이 어렵고 변경하는 일 자체가 위험을 수반한다.

## 하드웨어는 세부사항이다.
- 소프트웨어에게는 어떻게 데이터가 저장되는지 드러내지 않는다.

## 프로세서는 세부사항이다.
- 프로세서에 의존한다면 다른 프로세서에서 사용하지 못할 것이다.

## 운영체제는 세부사항이다.
- 새로운 os가 제공하는 이전 os와는 다른 기능과 시스템 명령어에 맞게 그 의미 자체를 조정해야 할 가능성이 높다.

## 인터페이스를 통하고 대체 가능성을 높이는 방향으로 프로그래밍하라
## DRY 원칙 : 조건부 컴파일 지시자를 반복하지 말라
- 하드웨어 추상화 계층이 있다면 하드웨어 유형은 HAL 뒤에 가려진 세부사항이 될 것이다. 만약 이 HAL이 조건부 컴파일 대신 사용할 수 있는 일련의 인터페이스를 제공한다면, 우리는 링커 또는 어떤 형태의 실시간 바인딩을 사용해서 소프트웨어를 하드웨어와 연결할 수 있다.

# 결론
- 모든 코드가 펌웨어가 되도록 내버려두면 제품이 오래 살아남을 수 없게된다.

















