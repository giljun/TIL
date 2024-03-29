# SQLD_ORDER BY 절

- ORDER BY 절에 칼럼명 대신 SELECT 절에서 사용한 ALIAS 명이나 칼럼 순서를 나타내는 정수도 사용 가능
- 기본적인 정렬 순서는 오름차순, SQL 문장의 제일 마지막에 위치
- 숫자형 데이터 타입은 오름차순으로 정렬했을 경우에 가장 작은 값부터 출력
- 날짜형 데이터 타입은 오름차순으로 정렬했을 경우 날짜 값이 가장 빠른 값이 먼저 출력
- Oracle에서는 NULL 값을 가장 큰 값으로 간주
- 반면, SQL Server에서는 NULL 값을 가장 작은 값으로 간주
- 칼럼 번호를 사용해서 정렬하는 것은 향후 유지보수성이나 가독성이 떨어지므로 가능한 칼럼명이나 ALIAS 명 권고
- 서브쿼리의 SELECT 절에서 선택되지 않은 칼럼들은 계속 유지되는 것이 아니라 서브쿼리 범위를 벗어나면 더 이상 사용할 수 없게 된다.
- GROUP BY 절에서 그룹핑 기준을 정의하게 되면 데이터베이스는 일반적인 SELECT 문장처럼 FROM 절에 정의된 테이블의 구조를 그대로 가지고 가는 것이 아니라, GROUP BY 절의 그룹핑 기준에 사용된 칼럼과 집계 함수에 사용될 수 있는 숫자형 데이터 칼럼들의 집합을 새로 만든다.



## SELECT 문장 실행 순서

- SELECT 칼럼명 ALIAS명

- FROM 테이블명

- WHERE 조건식

- GROUP BY 칼럼이나 표현식

- HAVING 그룹조건식

- ORDER BY 칼럼이나 표현식

  1. 발췌 대상 테이블을 참조한다.(FROM)

  2. 발췌 대상 데이터가 아닌 것은 제거한다.( WHERE )

  3. 행들을 소그룹화 한다. (GROUP BY)

  4. 그룹핑된 값의 조건에 맞는 것만을 출력한다. (HAVING)

  5. 데이터 값을 출력/계산한다.( SELECT )

     - 옵티마이저가 SQL 문장의 SYNTAX, SEMANTIC 에러를 점검하는 순서
     - FROM 절에 정의되지 않은 칼럼을 WHERE, GROUP BY, HAVING, SELECT, ORDER BY 절에 사용하면 에러 발생

     

## TOP N 쿼리

- ROWNUM
  - 순위가 높은 N개의 로우를 추출하기 위해 ORDER BY 절과 WHERE 절의 ROWNUM 조건을 같이 사용하는 경우가 있는 이 두 조건으로는 원하는 결과를 얻을 수 없다.
    - 급여 순서와 상관없이 무작위로 추출된 3명에 한해서 급여를 내림차순으로 정렬
- TOP N 쿼리의 결과를 만듬
  - 인라인 뷰에서 먼저 데이터 정렬을 수행한 후 메인쿼리에서 ROWNUM 조건을 사용하면, 위의 문제를 해결할 수 있다.
- TOP()
  - SQL Server는 TOP 조건을 사용하게 되면 별도 처리 없이 관련 ORDER BY 절의 데이터 정렬 후 원하는 일부 데이터만 쉽게 출력
  - TOP 절을 사용하여 결과 집합으로 반환되는 행 수를 제한할 수 있다.
  - WITH TIES 옵션은 ORDER BY 절의 조건 기준으로 TOP N의 마지막 행으로 표시되는 추가 행의 데이터가 같을 경우
    - N+ 동일 정렬 순서 데이터를 추가 반환하도록 지정하는 옵션

