# 24장 부분적 경계
### 경계를 나누기에 너무 많은 리소스가 들어간다면 부분적 경계를 만들어 보자!

## 마지막 단계를 건너뛰기
- 쌍방향 인터페이스도 그 컴포너트에 있고, 입력 출력 데이터 구조도 거기에 있으며, 모든 것이 완전히 준비되어 있다. 하지만 이 모두를 단일 컴포넌트로 컴파일해서 배포한다.
- 다수의 컴포넌트를 관리하는 작업은 하지 않아도 된다.
- 시간이 흐르면서 별도로 분리한 웹 컴포넌트가 재사용될 가능성은 전혀 없을 것임이 명백해지고, 웹 컴포넌트와 위키 컴포넌트 사이의 구분도 약화되기 시작했다. 이 둘을 다시 분리하는 작업이 생길 것이다.

## 일차원 경계
- 미래에 필요한 아키텍처 경계를 위한 무대를 마련한다는 점에서 이점이 있다.
- 매우 빠르게 붕괴될 수 있다는 점 역시 분명..

## 퍼사드
- 의존성 역전을 포기하고 퍼사드 클레스를 만들고 클라이언트에서 해당 퍼사드를 참조하도록 하자...
- 비밀 통로 또한 쉽게 만들 수 있다..

# 25장 계층과 경계
- 흐름이 항상 2가지만 존재하지는 않는다.
- 비즈니스 로직은 흐름에서 최종적으로 처리되는 곳이 된다.
- 경계를 너무 오버엔지리어링해서 나누는 것도 좋지 못하지만 필요한 순간에 구현하는 것도 구현을 어렵게 만들 수 있다. 적당하게 예측하여 적당하게 구현하자.

# 26장 메인 컴포넌트
- 메인 컴포넌트는 궁극적인 세부사항으로, 가장 낮은 수준의 정책이다. 메인은 시스템의 초기 진입접이다. 운영체제를 제외하면 어떤 것도 메인에 의존하지 않는다. 메인은 모든 팩토리와 전략 그리고 시스템 전반을 담당하는 나머지 기반 설비를 생선한 후, 시스템에서 더 높은 수준을 담당하는 부분으로 제어권을 넘기는 역할을 맡는다.
- 요지는 메인은 클린 아키텍처에서 사장 바깥 원에 위치하는 지저분한 저수준 모듈이라는 점이다. 에인은 고수준의 시스템을 위한 모든 것을 로드한 후, 제어권을 고수준의 싯,템에게 넘긴다.