# 30장 데이터베이스는 세부사항이다.
## 아키텍처 관점에서 볼 때 데이터베이스는 엔티티가 아니다.

## 관계형 데이터베이스
- 관계형 테이블은 특정한 형식의 데이터에 접근하는 경우에는 편리하지만, 데이터를 테이블에 행 단위로 배치한다는 자체는 아키텍처적으로 볼 때 전혀 중요하지 않다. 애플리케이션의 유스케이스는 이러한 방식을 알아서는 안되며 관여해서도 안된다.

## 데이터베이스 시스템은 왜 이렇게 널리 사용되는가?
- 지난 반세기 동안 회전식 자기 디스크는 데이터 저장소의 중심에 있었다.
- 디스크 지연 완화, 데이터를 표현하는 표준적인 방식이 필요
- 파일 시스템, 관계형 데이터베이스 관리 시스템이 분리되어 자리를 잡음.

## 디스크가 없다면 어떻게 될까?
- 사실 이 문제를 곰곰이 생각해 보면, 당신은 이미 이렇게 일하고 있다는 사실을 알아챌 것이다. 데이터가 데이터베이스나 파일 시스템에 있더라도, ram으로 읽은 후에는 다루기 편리한 형태로 그 구조를 변경한다. 리스트 집합 스택 큐 등 입맛에 맞는 구조로 말이다. 데이터를 파일이나 테이블 형태로 그대로 두는 경우는 거의 없다.

## 세부사항
- 데이터베이스는 그저 메커니즘에 불과하며, 디스크 표면과 ram사이에서 데이터를 이리저리 옮길 때 사용할 뿐이다.

## 성능은?
- 성능은 아키텍처와 관련된 관심사가 아닌가? 당연히 아키텍처적인 관심사다. 하지만 데이터 저장소의 측면에서 성능은 완전히 캠슐화하여 업무 규칙과는 분리할 수 있는 관심사다. 성능은 시스템의 전반적인 아키텍처와는 아무런 관련이 없다.

### 데이터는 중요하다. 데이터베이스는 세부사항이다.

# 31장 웹은 세부사항이다.
## 끝없이 반복하는 추
- 앞으로도 우리는 연산 능력을 어디에 둘지 알 수 없을 것이다. 연산 능력을 중아에 집중하는 방식과 분산하는 방식 사이에서 우리는 끊임없이 움직인다.
- 이런 변화에 휘둘리지 않고 비즈니스 로직을 분리하면 쉽게? 대응이 가능할 것이다.

# 32장 프레임워크는 세부사항이다.
## 혼안 관계의 비대칭성
- 당신과 프레임워크 제작사 사이의 관계는 놀라울 정도로 비대칭적이다. 당신은 프레임워크를 위해 대단히 큰 헌신을 해야 하지만, 프레임워크 제작사는 당신을 위해 아무런 헌신도 하지 않는다.

- 프레임워크 제작사 입장에서는 프레임워크와 이러한 결합이 위험 요소가 되지 않는다. 오히려 프레임워크와 결합되기를 바란다. 왜냐하면 제작자는 그 프레임워크에 대해 절대적인 제어권을 쥐고 있기 때문이다.
- 사실상 프레임워크 제작사는 당신에게 프레임워크와 혼인하기를 요구하는 것이다. 즉 프레임워크에 대해 장기간 걸친 막대한 헌신을 요청하는 것이다. 그럼에도 프레임워크 제작자는 어떠한 경우에도 그에 상응하는 헌신을 당신에게 하지는 않을 것이다. 이 혼인 관계는 일방적이다. 모든 위험과 부다음 오롯이 당신이 감수할 뿐, 제작자가 감수하는 건 아무것도 없다.

## 위험 요인
- 프레임워크의 아키텍처는 그다지 깔끔하지 않은 경우가 많다.
- 프레임워크는 애플리케이션의 초기 기능을 만드는 데는 도움이 될. 것이다. 하지만 제품이 성숙해지면서 프레임워크가 제공하는 기능과 틀을 벗어나게 될 것이다.
- 프레임워크는 당신에게 도움되지 않는 방향으로 진화할 수도 있다.
- 새롭고 더 나은 프레임워크가 등장해서 갈아타고 싶을 수도 있다.

## 해결책

- 프레임워크를 사용할 수는 있다. 다만 프레임워크와 적당히 거리를 두자.
- 프레임워크가 아키텍처의 안쪽 원으로 들어오지 못하게 하라


















