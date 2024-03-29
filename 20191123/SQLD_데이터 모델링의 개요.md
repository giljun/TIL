# SQLD_데이터 모델링의 개요

## 성능 데이터 모델링의 정의

- 데이터의 용량이 커지고 기업의 의사결정의 속도가 빨라질수록 데이터를 처리하는 속도는 빠르게 처리되어야 할 필요성을 반증
- 성능이 저하되는 데이터 모델링의 경우, 크게 세 가지 경우를 고려하여 성능을 향상시킬 수 있다.
  - 데이터 모델 구조에 의해 성능 저하
  - 데이터가 대용량이 됨으로 인해 불가피하게 성능 저하
  - 인덱스 특성을 충분히 고려하지 않고 인덱스를 생성함으로 인해 성능 저하
- 성능 데이터 모델링이 단순히 반정규화만을 의미하지 않음을 주목해야 한다.
  - 성능 데이터 모델링은 정규화를 통해서도 수행할 수 있고
  - 인덱스의 특징을 고려해서 칼럼의 순서도 변형할 수 있다.
  - 대량의 데이터 특성에 따라 비록 정규화된 모델이라도 테이블을 수직 또는 수평 분할하여 적용하는 방법도 있고
  - 논리적인 테이블을 물리적인 테이블로 전환할 때 데이터 처리의 성격에 따라 변환하는 방법도
  - 성능 데이터 모델링의 범주에 포함



## 성능 데이터 모델링 수행시점

- 성능 향상을 위한 비용은 프로젝트 수행 중에 있어서 사전에 할수록 비용이 들지 않는다.
- 특히 분석/설계 단계에서 데이터 모델에 성능을 고려한 데이터 모델링을 수행할 경우, 성능 저하에 따른 재업무 비용을 최소화 할 수 있는 기회를 가지게 된다.



## 성능 데이터 모델링 고려사항

1. 데이터 모델링을 할 때 정규화를 정확하게 수행
2. 데이터베이스 용량산정을 수행
3. 데이터베이스에서 발생되는 트랜잭선의 유형을 파악
4. 용량과 트랜잭션의 유형에 따라 반정규화를 수행
5. 이력모델의 조정, PK/FK 조정, 슈퍼타입/서브타입 조정 등을 수행
6. 성능관점에서 데이터 모델을 검증





