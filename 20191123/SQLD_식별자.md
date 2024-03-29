# SQLD_식별자

## 식별자 개념

- 엔터티를 구분짓는 논리적인 이름
- 엔터티를 대표할 수 있는 속성
- 반드시 하나의 유일한 식별자가 존재



## 식별자의 특징

- 주식별자에 의해 엔터티내에 모든 인스턴스들이 유일하게 구분되어야 한다.
  - 사원번호처럼 개인별로 고유하게 부여
- 주식별자를 구성하는 속성의 수는 유일성을 만족하는 최소의 수가 되어야 한다.
  - 사원번호만으로도 고유한 구조인데, 사원분류코드+사원번호로 식별자가 구성될 경우, 부절한 주식별자 구조
- 지정된 주식별자의 값은 자주 변하지 않는 것이어야 한다.
  - 사원번희 값이 변한다는 의미는 이전기록이 말소되고 새로운 기록이 발생되는 개념
- 주식별자가 지정이 되면 반드시 값이 들어와야 한다.
  - 사원번호 없는 회사직원은 있을 수 없다.



## 식별자 분류 및 표기법

### 대표성 여부

- 주식별자
  - 엔터티 내에서 각 어커런스를 구분할 수 있는 구분자
  - 타 엔터티와 참조관계를 연결할 수 있는 식별자
- 보조식별자
  - 엔터티 내에서 각 어커런스를 구분할 수 있는 구분자
  - 타 엔터티와 참조관계를 연결할 수 없는 식별자

### 스스로 생성여부

- 내부식별자
  - 엔터티 내부에서 스스로 만들어지는 식별자
- 외부식별자
  - 타 엔터티와의 관계를 통해 타 엔터티로부터 받아오는 식별자

### 속성의 수

- 단일식별자
  - 하나의 속성으로 구성된 식별자
- 복합식별자
  - 둘 이상의 속성으로 구성된 식별자

### 대체여부

- 본질식별자
  - 업무에 의해 만들어지는 식별자
- 인조식별자
  - 업무적으로 만들어지지는 않지만 원조식별자가 복잡한 구성을 가지고 있기 때문에 인위적으로 만든 식별자



## 주식별자 도출 기준

- 해당 업무에서 자주 이용되는 속성을 지정한다.
- 명칭, 내역 등과 같이 이름으로 기술되는 것들은 피한다
  - 엔터티에서 구분자가 존재하지 않을 경우 새로운 식별자를 생성한다.
    - 일련번호, 코드
- 복합으로 주식별자로 구성할 경우, 너무 많은 속성이 포함되지 않도록 한다.
  - 주식별자의 개수가 많을 경우 새로운 인조식별자를 생성한다.



## 식별자관계와 비식별자관계에 따른 식별자

### 식별자관계와 비식별자 관계의 결정

- 외부식별자는 자기 자신의 엔터티에서 필요한 속성이 아니라 다른 엔터티와의 관계를 통해 자식 쪽 엔터티에 생성되는 속성을 말함.
  - Foreign Key 역할을 한다.
  - 관계와 속성을 정의하고 주식별자를 정의하면, 논리적인 관계에 의해 자연스럽게 외부식별자가 도출되지만, 중요하게 고려해야할 사항이 있다.
  - 엔터티에서 주식별자가 지정되고 엔터티간 관계를 연결하면 부모쪽의 주식별자를 자식엔터티의 속성으로 내려 보낸다. 
  - 이 때 자식 엔터티에서 부모엔터티로부터 받은 외부식별자를 자신의 주식별자로 이용할 것인지 또는 부모와 연결이 되는 속성으로서만 이용할 것인지를 결정해야 한다.

### 식별자관계

- 자식엔터티의 주식별자로 부모의 주식별자가 상속되는 경우를 말한다.
- Null값이 오면 안된다.
- 1:1 관계
  - 부모로부터 받은 속성을 자식엔터티가 모두 사용하고 그것만으로 주식별자로 사용할 경우
- 1:M  관계
  - 부모로부터 받은 속성, 다른 부모엔터티에서 받은 속성, 스스로 가진 속성으로 주식별자가 구성된 경우

### 비식별자관계

- 부모엔터티로부터 속성을 받았지만 자식엔터티의 주식별자로 사용하지 않고 일반적인 속성으로 사용하는 경우
  - 자식엔터티에서 받은 속성이 반드시 필수가 아니기에 부모 없는 자식이 생성될 수 있는 경우
  - 엔터티별로 데이터의 생명주기를 다르게 관리할 경우
  - 여러 개의 엔터티가 하나의 엔터티로 통합되어 표현되었는데 각각의 엔터티가 별도의 관계를 가질 경우
  - 자식엔터티에서 별도의 주식별자를 성생하는 것이 더 유리할 경우

### 식별자 관계로만 설정할 경우의 문제점

- 식별자관계로만 연결된 모델의 경우 주식별자 속성이 지속적으로 증가한다.
- 주식별자 증가로 복잡성과 오류가능성을 유발시킬 수 있다.

### 비식별자 관계로만 설정할 경우의 문제점

- 속성이 자식엔터티로 상속되지 않는다.
- 속성이 자식엔터티로 상속되지 않아 부모엔터티까지 조인되는 현상이 발생
- 불필요한 조인이 발생되고 SQL구문도 길어져 성능 저하 현상이 발생

### 식별자관계와 비식별자관계 모델링

- 비식별자관계 선택 프로세스
  - 다음 조건에 해당할 경우 비식별자관계로 조정하면 된다.
  - 관계분석 → 관계의 강/약 분석(약한 관계) → 자식테이블 독립 PK 필요(독립 PK구성) → SQL복잡도 증가/개발 생산성 저하(PK속성 단순화)
- 식별자와 비식별자관계 비교
  - 식별자관계
    - 강한 연결관계 표현
    - 자식 주식별자의 구성에 포함
    - 실선 표현
    - 반드시 부모엔터티 종속
    - 자식 주식별자구성에 부모 주식별자포함 필요
    - 상속받은 주식별자속성을 타 엔터티에 이전 필요
  - 비식별자관계
    - 약한 연결관계 표현
    - 자식 일반속성에 포함
    - 점선 표현
    - 약한 종속관계
    - 자식 주식별자구성을 독립적으로 구성
    - 자식 주식별자구성에 부모 주식별자 부분 필요
    - 상속받은 주식별자속성을 타 엔터티에 차단 필요
    - 부모쪽의 관계참여가 선택관계











