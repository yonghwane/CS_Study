# DataBases Study

# Quiz는 이쪽으로 🌐

-   [SQL공부를 위한 문제정리](./DataStructures_quiz.md)

# 데이터 베이스의 종류

## 1. Key-Value Database

Key와 Value의 쌍으로 데이터를 저장한다. 예를 들어:

| Key  | Value  |
| ---- | ------ |
| 이름 | 홍길동 |
| 나이 | 20     |

이전에는 자주 사용되지 않았지만, 최근에는 RAM에 데이터를 저장하는 Redis와 같은 데이터베이스가 등장하면서 사용 빈도가 늘었다.

주로 사용되는 곳:

-   데이터 캐싱
-   채팅을 위한 pub/sub
-   영상 스트리밍
-   로그인 기록 저장

## 2. Relational Database (관계형 데이터베이스)

테이블을 만들고, 각 행에 데이터를 저장한다. 대표적으로 Oracle, MySQL, PostgreSQL, MariaDB 등이 있다.

이 데이터베이스를 사용하려면 SQL 문법을 알아야 하는데, 여기서 중요한 점은 데이터를 정규화하여 저장해야 하며, 이를 통해 데이터 중복을 방지해야한다. ACID 트랜잭션 기능이 있어 안정성을 높일 수 있다. 주로 데이터의 정확도를 높이는 데 사용된다.

## 3. Document Database

Collection이라는 폴더를 만들고, 그 안에 Document를 만들어 데이터를 JSON 형태로 저장합니다. 데이터의 중복 제거가 필요 없으며, 데이터의 정규화를 할 필요가 없다. 또한, 데이터의 분산 처리를 잘 할 수 있다는 특징이 있다.

## 요약

1. 일반적으로 사용되는 데이터베이스의 종류는 Relational Database와 Document Database 두가지 종류가 주로 사용된다.
2. 입출력이 많으면 Document Database를, 정확도와 일관성이 중요하면 Relational Database를 사용한다.
3. 정확도와 일관성이 중요하면 Relational Database를 사용한다.

# DBMS (DataBase Management System)

데이터베이스를 관리하기 위한 도구로. 주요 기능은 다음과 같다:

1. 데이터 입출력을 쉽게한다.
2. DB 접속 계정 발급을 용이하게 한다.
3. 데이터베이스 백업을 쉽게 해준다.

# MySQL 조작 방법

데이터 조작 시에는 다음과 같은 방법을 사용할 수 있다:

1. MySQL Workbench를 사용.
2. 터미널을 이용하여 데이터베이스를 직접 조작.
3. DBeaver를 이용.

# 테이블 만드는 방법

데이터베이스를 컴퓨터의 폴더에 비유하면, 테이블은 그 폴더에 들어있는 파일에 해당한다. 즉, 다음과 같이 생각하면 좋다.:

-   데이터베이스 = 폴더
-   테이블 = 파일

# 신규 테이블 작성 방법

테이블을 작성할 때는 테이블의 구조를 미리 정의해야 하는데, 테이블에 어떤 컬럼이 들어갈지 미리 정의를 해줘야 한다. 여기서 세로 줄은 컬럼, 가로 줄은 행에 해당한다.이 Column을 정의할 때 그에 동반되는 Column Data type도 잘 선택을 해줘야한다.

# DataBase의 Data-type

-   문자형
    char
    varchar
    text
    tinytext
    mediumtext
    longtext
    여기서 일반적으로는 varchar를 선택하면 된다. 혹시나 정말 긴 문자를 선택할때는 mediumtext, longtext를 선택한다.
    또한 varchar뒤에 숫자가 varchar(50)이런식으로 들어가있는데. 이는 문자의 총허용길이를 나타낸다.

-   숫자타입
    SMALLINT
    MEDIUMINT
    INT
    BIGINT
    FLOAT
    DOUBLE
    DECIMAL
    여기서 보통은 INT또는, BIGINT를 쓴다
-   날짜/시간을 나타내는 데이터타입
    DATE: YYYY-MM--DD의 형식으로 저장이 된다.
    TIME: HH:MM:DD의 형식으로 저장이 된다.
    DATE/TIME: YYYY-MM-DD HH:MM:SS 형식으로 저장이 된다.

# SQL(Structured Query Language)

데이터베이스 조작에 필요한 언어,이 SQL을 통해서

-   데이터 삽입
-   데이터 출력
-   데이터 삭제
-   데이터 수정
    등과 같은 작업을 수행할 수 있고 더 나아가서 프로그래밍을 통한 특정 데이터를 가공할 수도 있다.

# 자주쓰는 cmd sql문 
  -  데이터베이스 접속
  mysql -u root - p -P 원하는 포트
  -  데이터베이스 목록보기
  SHOW DATABASES
  -  특정 데이터베이스 선택
  USE DATABASES
  -  데이터베이스 생성
  CREATE DATABASE 원하는이름
  -  데이터베이스 삭제
  DROP DATABASE 원하는이름
  -  현재 어떠한 포트를 쓰고 있는지 확인하는 법
  Window + R 을 눌러서 resmon.exe를 실행
  -  해당포트를 종료하는법
  해당하는 PID를 찾아서 명령어 프롬프트 창에서 taskkill -f -pid 해당하는번호

# 데이터 출력 및 정렬하는 팁

**SELECT 칼럼이름 FROM 테이블이름**
을 하면 테이블의 특정 칼럼을 불러 올 수 있고

**SELECT 칼럼이름, 칼럼이름2 FROM 테이블이름**
와 같은 방식으로 여러가지 컬럼들도 불러 올 수 있고

**SELECT \* FROM 테이블이름**
와 같이 모든 칼럼들을 불러 올 수도 있다.
하지만 단순히 출력만 하는 것은 의미가 없는데, 이를 정렬하는 방법으로써는

**SELECT \* FROM 테이블이름 ordert by 컬럼명 ASC/DESC**
여기서 asc는 오름차순, desc는 내림차순으로 정렬하겠다는 뜻이다.

**원하는 행만 추가하는법(필터링)**

WHERE 조건식
예시)SELECT \* FROM 테이블 WHERE 칼럼값 = "값"
여기서는 =, !=, >, <. >=, <= 과 같은 비교연산자를 사용할 수 도 있고, 문자열에도 사용을 할 수가 있는데
예를들어, "가" < "나", "나" < "다" 와 같은 비교연산자는 TRUE가 된다.

**BETWEEN / AND 연산자**

원래 가격이 5000 < 가격 < 8000와 같이 수학등에서는 표현하지만, SQL에서는 이것이 통용되지 않는다.
이때 A < 가격 < B를 표현하고 싶으면, 컬럼명 BETWEEN A AND B라고 작성을 해야한다
즉 5000< 가격 < 8000이면 -> BETWEEN 5000 AND 8000과 같이 작성한다.
여기서 AND는 좌우조건 둘다 해당하는 조건, OR은 둘중에 하나를 의미한다
여기서 카테고리가 '가구'거나 '옷' 둘중에 하나에서 가격은 5000원인 것을 찾고싶을 경우
SELECT \* FROM pruduct WHERE (카테고리 = '가구' OR 카테고리 = '옷') AND 가격 = 5000; 으로 작성해주면 된다

**특정단어가 포함된 값들을 검색해서 그값들만 필터링하는 방법**

SELECT \* FROM product WHERE 상품명 LIKE %소파%
와 같이 %%안에 내가 원하는 값들을 넣어주면 되는데, *도 같은 기능을 하는데
둘의 차이점은 %은 아무문자, *는 아무문자 1자만된다.

-   주의점  
    검색을 할때 %를검색하고싶은 문자앞에다가 써서 해버리면 나중에 index활용을 못한다.
    %, LIKE등은 VARCHAR()에 주로 사용되고, CHAR()타입에는 사용을 할 수 없다.

**SQL의 집계함수**

최소값 -> min()
최대값 -> max()
평균값 -> avg()
총합 -> sum()
행렬수 -> count()
등이 있으며, 집계 함수들은 보통 정수형, 숫자들만 작성할 수 있다.

**AS문법**
as문법을 사용하면 컬럼명을 바꿔서 출력이 가능하다.
예를들어, SELECT MAX(사용금액) AS 작명 FROM card
와 같이 작성하면 사용금액의 최대값을 찾아서 그 값의 컬럼이름을 작명을 한다.

**최소, 최대 값을 구하는 또다른 방법**

최소,최댓값을 구할때 min(), max()말고도 정렬하는 order by 사용금액 asc/desc limit 1을 하면 그값 하나만 구해날 수 있다

**컬럼끼리의 사칙연산**

SELECT column1 \* column2 from card
와 같은 방식으로 정수인경우에는 둘의 값을 연산해서 출력할 수 도 있다.

# 문자열 연산

문자열도 연산이 가능합. 예를 들어, 두 컬럼의 문자열을 합치려면 `CONCAT` 함수를 사용가능:

```sql
CONCAT(컬럼명1, 컬럼명2)
```
또한, TRIM 함수를 사용하면 문자열의 좌우 공백을 제거할 수 있고, REPLACE 함수를 사용하면 특정 문자열을 다른 문자열로 대체할 수 있다.


```
SELECT REPLACE(공백을제거할 컬럼명, ' ', '') FROM 제거하고싶은 테이블;
```

# 서브쿼리

쿼리문을 여러번 쓰는게 귀찮으면, 하나로 합쳐서 사용할 수 있다.(필수사항은 아니며, 그냥 귀찮을때 편하게 쓰면 좋음) 
사용 할 수 있는 조건은
  (1)1개의 데이터만 뱉는 쿼리문에만 서브쿼리를 작성 가능.
  (2)소괄호를 꼭 작성해주어야만 한다.

  ```
  -- 서브쿼리를 사용하지 않을 경우
  SELECT avg(사용금액) FROM card;  -- 결과값 
  SELECT * FROM card WHERE 사용금액 > 결과값;

  -- 서브쿼리를 사용할 경우
  SELECT * FROM card WHERE 사용금액 > (SELECT avg(사용금액) FROM card);
  ```

# GROUP BY
  GROUP BY 칼럼명 을 하면 컬럼의 같은 값을 모아준다.
  보통 GROUP BY를 사용하는경우는, 카테고리 컬럼에 해당하며, 이같은 것을 모아준 후 집계함수같은 것을 사용해서 통계를 내어주면좋다.

**HAVING**
  HAVING은 *GROUP BY결과*를 필터링 하고자 할때 사용, WHERE은 *테이블의 행*을 필터링할때 주로사용하므로 차이점에 대해 인지해두자.

# DDL(Data Definition Language)

DDL은 DB, 테이블, 컬럼 등의 생성/수정/삭제 문법들을 뜻한다.

1. **데이터베이스 생성**
    ```sql
    CREATE DATABASE 작명;
    ```

2. **데이터베이스 삭제**
    ```sql
    DROP DATABASE 작명;
    ```

3. **테이블 작성**
    ```sql
    CREATE TABLE 원하는데이터베이스명.원하는테이블의이름작명 (
        컬럼명1 int,
        컬럼명2 varchar(100),
        컬럼명3 int
    );
    ```

4. **테이블 삭제**
    ```sql
    DROP TABLE 해당하는데이터베이스.작명;
    ```

5. **해당하는 테이블에 컬럼을 추가/수정/삭제**
    ```sql
    ALTER TABLE 해당하는테이블명 ADD 칼럼명 데이터타입;
    ALTER TABLE 해당하는테이블명 MODIFY COLUMN 칼럼명 변경하고싶은 데이터타입;
    ALTER TABLE 해당하는테이블명 DROP COLUMN 칼럼명;
    ```

 반대로, `SELECT` 등 데이터를 다루는 문법은 DML(DATA Manipulation Language)라고 한다.

---


