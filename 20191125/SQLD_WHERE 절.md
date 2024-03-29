# SQLD_WHERE 절

- 사용자들은 자신이 원하는 자료만을 검색하기 위해서 SQL 문장에 WHERE 절을 이용하여 자료들에 대하여 제한
- WHERE 절에 조건이 없는 FTS 문장은 SQL 튜닝의 1차적인 검토 대상이 된다.
  - 무조건 나쁜 것은 아니며, 병렬 처리 등을 이용해 유용하게 사용하는 경우도 많다.



## 연산자의 종류

|       구분       |       연산자        |                       연산자의 의미                        |
| :--------------: | :-----------------: | :--------------------------------------------------------: |
|    SQL 연산자    |   BETWEEN a AND b   |      a와 b의 값 사이에 있으면 된다(a와 b 값이 포함됨)      |
|                  |         IN          |    리스트에 있는 값 중에서 어느 하나라도 일치하면 된다.    |
|                  |  LIKE '비교문자열'  |        비교문자열과 형태가 일치하면 된다.(%, _사용)        |
|                  |       IS NULL       |                       NULL 값인 경우                       |
| 부정 비교 연산자 |         !=          |                         같지 않다.                         |
|                  |         ^=          |                         같지 않다.                         |
|                  |         <>          |                         같지 않다.                         |
|                  |    NOT 칼럼명 =     |                       ~와 같지 않다                        |
|                  |    NOT 칼럼명 >     |                      ~보다 크지 않다.                      |
| 부정 SQL 연산자  | NOT BETWEEN a AND b | a와 b의 값 사이에 있지 않다. ( a와 b 값을 포함하지 않는다) |
|                  |       NOT IN        |                 list 값과 일치하지 않는다.                 |
|                  |     IS NOT NULL     |                   NULL 값을 갖지 않는다.                   |



## 문자 유형간의 비교 방법

| 구분                                                | 비교 방법                                                    |
| --------------------------------------------------- | ------------------------------------------------------------ |
| 비교 연산자의 양쪽이 모두 CHAR 유형 타입인 경우     | 길이가 서로 다른 CHAR형 타입이면 작은 쪽에 SPACE를 추가하여 길이를 같게 한 후에 비교한다. |
|                                                     | 서로 다른 문자가 나올 때까지 비교한다.                       |
|                                                     | 달라진 첫 번째 문자의 값에 따라 크기를 결정한다.             |
|                                                     | BLANK의 수만 다르다면 서로 같은 값으로 결정한다.             |
| 비교 연산자의 어느 한 쪽이 VARCHAR 유형 타입인 경우 | 서로 다른 문자가 나올 때까지 비교한다.                       |
|                                                     | 길이가 다르다면 짧은 것이 끝날 때까지만 비교한 후에 길이가 긴 것이 크다고 판단한다. |
|                                                     | 길이가 같고 다른 것이 없다면 같다고 판단한다.                |
|                                                     | VARCHAR는 NOT NULL까지 길이를 말한다.                        |
| 상수값과 비교할 경우                                | 상수 쪽을 변수 타입과 동일하게 바꾸고 비교한다.              |
|                                                     | 변수 쪽이 CHAR 유형 타입이면 CHAR 유형 타입의 경우를 적용한다. |
|                                                     | 변수 쪽이 VARCHAR 유형 타입이면 위의 VARCHAR 유형 타입의 경우를 적용한다. |



## 연산자의 우선순위

| 연산 우선순위 |            설 명             |
| :-----------: | :--------------------------: |
|       1       |           괄호 ()            |
|       2       |          NOT 연산자          |
|       3       | 비교 연산자, SQL 비교 연산자 |
|       4       |             AND              |
|       5       |              OR              |



## ROWNUM, TOP 사용

### ROWNUM

- WHERE 절에서 행의 개수를 제한하는 목적으로 사용



### TOP 절

- 결과 집합으로 출력되는 행의 수를 제한할 수 있다.