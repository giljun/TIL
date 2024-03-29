# SQLD_SQL 기본 연습문제

## 문제 1.

> 다음 설명 중 맞는 것은 무엇인가?
>
> 1. 데이터베이스에는 단 한 개의 테이블만 존재할 수 있다.
> 2. 데이터베이스 내에 테이블이란 존재하지 않는다.
> 3. 아주 복잡한 자료도 테이블은 하나만 만드는 것이 바람직하다.
> 4. 모든 자료는 실질적으로 테이블에 저장이 되며, 테이블에 있는 자료들을 꺼내 볼 수 있다.



## 문제 1. 해설

- 데이터베이스에는 자료의 성격에 따라 N개의 테이블을 생성한다.
- 모든 자료들은 테이블에 입력되며 조회, 수정, 삭제 할 수 있다.
- 따라서, 답은 4번



## 문제 2.

> 데이터 유형에 대한 설명 중 틀린 것은 무엇인가?
>
> 1. CHAR 유형은 고정 길이 문자형이다.
> 2. VARCHAR 유형은 가변 길이 숫자형이다.
> 3. NUMERIC 유형은 숫자형 데이터를 표현한다.
> 4. DATE 유형은 날짜 데이터를 다룰 때 사용한다.



## 문제 2. 해설

- VARCHAR 유형은 가변 길이 문자형이다.
- 따라서 정답은 2번



## 문제 3. 

> 다음 중 테이블 명으로 가능한 것은 무엇인가?
>
> 1. EMP100
> 2. 100EMP
> 3. EMP-100
> 4. 100_EMP



## 문제 3. 해설

- 테이블명과 칼럼명은 반드시 문자로 시작해야 한다.
- A-Z, a-z, 0-9, _, $, # 사용가능
- 따라서, 답은 1번



## 문제 4.

> 데이터를 입력하기 위해 사용하는 SQL 명령어는 무엇인가?
>
> 1. CREATE
>
> 2. UPDATE
>
> 3. INSERT
>
> 4. ALTER



## 문제 4. 해설

- 데이터를 입력하기 위해서 INSERT 명령어를 사용한다.
- 따라서 답은 3번



## 문제 5.

> Commit과 Rollback의 장점으로 적합하지 않은 것은 무엇인가?
>
> 1. 데이터 무결성을 보장한다.
> 2. 영구적인 변경을 하기 전에 데이터의 변경 사항을 확인 가능
> 3. 영구적인 변경을 할 수 없게 한다.
> 4. 논리적으로 연관된 작업을 그룹핑하여 처리 가능.



## 문제 5. 해설

- 데이터 무결성 보장
- 영구적인 변경을 하기 전에 데이터의 변경 사항 확인 가능
- 논리적으로 연관된 작업을 그룹핑하여 처리 가능
- 따라서, 답은 3번



## 문제 6. 

> 다음 SQL 문장의 결과 출력되는 데이터는 무엇인가?
>
> ​		SELECT PLAYER_NAME 선수명, E_PLAYER_NAME 선수영문명
>
> ​		FROM PLAYER
>
> ​		WHERE E_PLAYER_NAME_LIKE '_A%';
>
> 	1. 선수의 영문 이름이 A로 시작하는 선수들의 이름
>  	2. 선수의 영문 이름이 A나 a로 시작하는 선수들의 이름
>  	3. 선수의 영문 이름의 두번째 문자가 A인 선수들의 이름
>  	4. 위치에 상관없이 선수의 영문 이름에 A를 포함하는 선수들의 이름



## 문제 6. 해설

- "-"와 "%"는 와일드카드(WILD CARD)로 하나의 글자, 또는 모든 문자를 대신하여 사용됨
- 두번째 문자인 대문자 A만 출력하게 된다.
- 따라서, 정답은 3번



## 문제 7. 

> 어떠한 데이터 타입도 사용이 가능한 집계 함수는 어느 것인가?
>
> 1. COUNT
> 2. SUM
> 3. AVG
> 4. STDDEV



## 문제 7. 해설

- 집계 함수는 집합에 대한 정보를 제공하므로 주로 숫자 유형에 사용된다.
- 문자, 날짜 유형에도 적용가능한 함수는 MAX, MIN, COUNT
- 따라서, 정답은 1번



## 문제 8.

> SQL 문장에서 집합별로 집계된 데이터에 대한 조회 조건을 제한하기 위해서 사용하는 절은 어느 것인가?
>
> 1. WHERE 절
> 2. GROUP BY 절
> 3. HAVING 절
> 4. FROM 절



## 문제 8. 해설

- 일반적인 데이터에 대한 제한 조건을 사용하기 위해서는 WHERE 절을 사용
- 그룹별로 집계 데이터에 대한 제한 조건을 사용하기 위해서는 HAVING 절을 사용
- 따라서, 정답은 3번



## 문제 9.

> 다음 SQL 문장의 결과 출력되는 데이터는 무엇인가?
>
> ​	SELECT PLAYER_NAME 선수명, POSITION 포지션, BACK_KO 백넘버
>
> ​	FROM PLAYER
>
> ​	ORDER BY PLAYER_NAME, POSITION, BACK_NO DESC;
>
> 	1. ORDER BY 1 DESC, 2, 백넘버
>  	2. ORDER BY 선수명, 2, DESC 백넘버
>  	3. ORDER BY PLAYER_NAME, 2, 3
>  	4. ORDER BY 선수명 ASC, 포지션, 3 DESC



## 문제 9. 해설

- ORDER BY 절에서 정렬 기준이 생략되면 DEFAULT ASC 정렬이 됨
- ORDER BY 절의 칼럼명 대신에 SELECT 절에 기술한 컬럼의 순서번호나 컬럼의 ALIAS를 사용할 수 있다.
- 따라서, 정답은 4번



## 문제 10.

> 다음 SQL 문장에서 틀린 부분은 어디인가?
>
> 	1. SELECT PLAYER, PLAYER_NAME 선수명, TEAM, TEAM_NAME 팀명
>  	2. FROM PLAYER P, TEAM T
>  	3. WHERE P.TEAM_ID = T.TEAM_ID
>  	4. ORDER BY 선수명



## 문제 10. 해설

- FROM 절 테이블에 ALIAS를 사용할 경우 중복된 이름이 있는 경우 SELECT 절에서는 반드시 ALIAS 명을 사용해야 한다.
- 따라서, 정답은 1번













