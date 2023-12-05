# DataBases Study 
# Quiz는 이쪽으로 🌐

-   [SQL공부를 위한 문제정리](./DataStructures_quiz.md)

# 데이터 베이스의 종류 
## 1. Key-Value Database 

Key와 Value의 쌍으로 데이터를 저장한다. 예를 들어:

| Key | Value |
|-----|-------|
| 이름 | 홍길동 |
| 나이 | 20    |

이전에는 자주 사용되지 않았지만, 최근에는 RAM에 데이터를 저장하는 Redis와 같은 데이터베이스가 등장하면서 사용 빈도가 늘었다.

주로 사용되는 곳:
- 데이터 캐싱
- 채팅을 위한 pub/sub
- 영상 스트리밍
- 로그인 기록 저장

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

- 데이터베이스 = 폴더
- 테이블 = 파일

# 신규 테이블 작성 방법

테이블을 작성할 때는 테이블의 구조를 미리 정의해야 하는데,  테이블에 어떤 컬럼이 들어갈지 미리 정의를 해줘야 한다. 여기서 세로 줄은 컬럼, 가로 줄은 행에 해당한다.이 Column을 정의할 때 그에 동반되는 Column Data type도 잘 선택을 해줘야한다.

# DataBase의 Data-type

  - 문자형 
     char
     varchar
     text
     tinytext
     mediumtext
     longtext
    여기서 일반적으로는 varchar를 선택하면 된다. 혹시나 정말 긴 문자를 선택할때는 mediumtext, longtext를 선택한다.
    또한 varchar뒤에 숫자가 varchar(50)이런식으로 들어가있는데. 이는 문자의 총허용길이를 나타낸다.
  
  - 숫자타입
     SMALLINT
     MEDIUMINT
     INT
     BIGINT
     FLOAT
     DOUBLE
     DECIMAL
     여기서 보통은 INT또는, BIGINT를 쓴다
    
  - 날짜/시간을 나타내는 데이터타입
     DATE: YYYY-MM--DD의 형식으로 저장이 된다.
     TIME: HH:MM:DD의 형식으로 저장이 된다.
     DATE/TIME: YYYY-MM-DD HH:MM:SS 형식으로 저장이 된다.

# SQL(Structured Query Language)
데이터베이스 조작에 필요한 언어,이 SQL을 통해서 
  - 데이터 삽입
  - 데이터 출력
  - 데이터 삭제
  - 데이터 수정
등과 같은 작업을 수행할 수 있고 더 나아가서 프로그래밍을 통한 특정 데이터를 가공할 수도 있다. 

# 데이터 출력 및 정렬하는 팁  

 **SELECT 칼럼이름 FROM 테이블이름**
 을 하면 테이블의 특정 칼럼을 불러 올 수 있고 

 **SELECT 칼럼이름, 칼럼이름2 FROM 테이블이름**
 와 같은 방식으로 여러가지 컬럼들도 불러 올 수 있고 

 **SELECT * FROM 테이블이름**
 와 같이 모든 칼럼들을 불러 올 수도 있다.
 하지만 단순히 출력만 하는 것은 의미가 없는데, 이를 정렬하는 방법으로써는 

  **SELECT * FROM 테이블이름 ordert by 컬럼명  ASC/DESC**
  여기서 asc는 오름차순, desc는 내림차순으로 정렬하겠다는 뜻이다.


