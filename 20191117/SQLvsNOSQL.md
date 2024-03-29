# SQL VS NOSQL

## SQL

- Structured Query Language의 약자
- 데이터베이스 자체를 나타내는 것이 아니라, 특정 유형의 데이터베이스와 상호 작용하는데 사용하는 언어
- 관계형 데이터베이스 관리 시스템에서 데이터를 저장, 수정, 삭제 및 검색할 수 있습니다.
- 관계형 데이터베이스에는 두 가지 주요 특징이 있습니다.
  - 정해진 데이터 스키마를 따라 데이터베이스 테이블에 저장됩니다.
  - 관계를 통해서 연결된 여러개의 테이블에 분산됩니다.
- 엄격한 스키마
  - 데이터는 테이블에 레코드로 저장
  - 각 테이블에는 명확하게 정의된 구조가 있다.
  - 스키마를 준수하지 않은 레코드는 추가할 수 없음
- 관계
  - 여러개의 테이블에 나누어서, 데이터들의 중복을 피할 수 있다.
  - 하나의 테이블에서 중복없이 하나의 데이터만을 관리하기 때문에, 다른 테이블에서 부정확한 데이터를 다룰 위험이 없습니다.



## NoSQL

- SQL과 반대되는 접근방식을 따르기 때문에 지어진 이름입니다.
- 스키마 없음
- 관계 없음
- 레코드를 문서(documents)라고 부릅니다.
  - JSON 데이터와 비슷한 형태를 가지고 있습니다.
- 다른 구조의 데이터를 같은 컬렉션( = SQL에서의 테이블 )에 추가할 수 있습니다.
- 조인이라는 개념이 존재하지 않는다.
- 컬렉션을 통해 데이터를 복제하여 각 컬렉션 일부분에 속하는 데이터를 정확하게 산출
- 데이터 중복으로 인한 불안정한 측면이 존재하나, 복잡하고 어떤 순간에는 느린 조인을 사용할 필요가 없다는 것입니다.
- 자주 변경되지 않은 데이터일 때 더 큰 장점이 있습니다.



## 수직적 & 수평적 확장

## 수직적 확장

- 단순히 데이터베이스의 서버의 성능을 향상시키는 것
- 데이터가 저장되는 방식 때문에 SQL 데이터베이스는 수직적 확장만을 지원합니다.



## 수평적 확장

- 더 많은 서버가 추가되고 데이터베이스가 전체적으로 분산되는 것을 의미
- 하나의 데이터베이스에서 작동하지만 여러 호스트에서 작동합니다.
- NoSQL 데이터베이스에서만 가능
- SQL 데이터베이스 '샤딩'의 개념을 알고 있지만 특정 제한이 있으며 구현하기가 대체로 어렵다
  - 그러나 NoSQL 데이터베이스는 이를 기본적으로 지원하므로 여러 서버에서 데이터베이스를 쉽게 분리할 수 있다.



## 어떤 데이터베이스 솔루션을 사용해야 할까요?

- 확실한 정답은 없다.
- SQL과 NoSQL은 모두 훌륭한 솔루션
- 선택의 문제는 어떤 데이터를 다루는지, 어떤 애플리케이션에서 사용되는지를 고려

- 각각의 주요 장점
  - SQL의 장점
    - 명확하게 정의된 스키마, 데이터 무결성 보장
    - 관계는 각 데이터를 중복없이 한번만 저장됩니다.
  - NoSQL의 장점
    - 스키마가 없기 때문에, 더 유연하다.
    - 언제든지 저장된 데이터를 조정하고 새로운 필드를 추가할 수 있다.
    - 데이터는 애플리케이션이 필요로 하는 형식으로 저장됩니다. 이렇게 하면 데이터를 읽어오는 속도가 빨라집니다.
    - 수직 및 수평 확장이 가능하므로 데이터베이스가 애플리케이션에서 발생시키는 모든 읽기 / 쓰기 요청을 처리할 수 있다.
- 각각의 주요 단점
  - SQL의 단점
    - 상대적으로 덜 유연합니다.
    - 데이터 스키마는 사전에 계획되고 알려져야 합니다.
    - 관계를 맺고 있기 때문에, JOIN문이 많은 매우 복잡한 쿼리가 만들어 질 수 있다.
    - 수평적 확장이 어렵고, 대체로 수직적 확장만 가능
    - 성장 한계 직면
  - NoSQL의 단점
    - 유연성 때문에, 데이터 구조 결정을 하지 못하고 미룰 수 있다.
    - 데이터 중복은 여러 개의 레코드가 변경된 경우 업데이트를 해야 한다.
    - 데이터가 여러 컬렉션에 중복되어 있기 때문에, 수정을 해야 하는 경우 모든 컬렉션에서 수행해야 함을 의미.
- 각각의 사용
  - SQL
    - 관계를 맺고 있는 데이터가 자주 변경되는 애플리케이션일 경우
    - 변경될 여지가 없고, 명확한 스키마가 사용자와 데이터에게 중요한 경우
  - NoSQL
    - 정확한 데이터 구조를 알 수 없거나 변경 / 확장 될 수 있는 경우
    - 읽기 처리를 자주 하지만, 데이터를 자주 변경하지 않는 경우
    - 데이터베이스를 수평으로 확장해야 하는 경우



