# SQL_Instruction_set
## 검색하기 귀찮아서 한번씩 써본 쿼리문은 여기에 적어놓을것임

## 기초적인 CRUD는 mysql 파일로 들어가면 있음


### DESC [테이블명];
### 테이블의 정보들을 정리해서 보여준다.

### RENAME TABLE [테이블명] TO [바뀔 테이블명];
### 테이블명 변경


## 테이블에 컬럼추가

ALTER TABLE topic_tag_relation ADD COLUMN tag_name VARCHAR(45) NULL AFTER tag_id;


## 추가한 컬럼에 컬럼값 추가

UPDATE topic_tag_relation SET tag_name = 'rdb' WHERE (topic_title = 'MySQL') and (tag_id='1');


## 동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요.

SELECT * FROM ANIMAL_INS ORDER BY ANIMAL_ID;


## 동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요.

SELECT NAME, DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC ;


## 동물 보호소에 들어온 동물 중 아픈 동물1의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.

SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION = 'Sick' ORDER BY ANIMAL_ID ASC;


## 동물 보호소에 들어온 동물 중 젊은 동물1의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.

SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION != 'Aged' ORDER BY ANIMAL_ID ASC


## 동물 보호소에 들어온 모든 동물의 아이디와 이름을 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요.

SELECT ANIMAL_ID, NAME FROM ANIMAL_INS ORDER BY ANIMAL_ID ASC;


## 동물 보호소에 들어온 모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회하는 SQL문을 작성해주세요. 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.

SELECT ANIMAL_ID, NAME, DATETIME FROM ANIMAL_INS ORDER BY NAME ASC, DATETIME DESC;


## 동물 보호소에 가장 먼저 들어온 동물의 이름을 조회하는 SQL 문을 작성해주세요.

SELECT NAME FROM ANIMAL_INS ORDER BY DATETIME ASC LIMIT 1;


## 가장 최근에 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.

SELECT MAX(DATETIME) FROM ANIMAL_INS ;
### MAX 함수를 쓰는게 편하긴 하지만 조회를 많이 하기 때문에 과부화가 올 수 있어 최적화된 방법이 따로 있다. 나중에 성장해서 쓰겠음..

##동물 보호소에 가장 먼저 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.

SELECT MIN(DATETIME) FROM ANIMAL_INS;


##동물 보호소에 동물이 몇 마리 들어왔는지 조회하는 SQL 문을 작성해주세요.

SELECT COUNT(*) FROM ANIMAL_INS;

## 동물 보호소에 들어온 동물의 이름은 몇 개인지 조회하는 SQL 문을 작성해주세요. 이때 이름이 NULL인 경우는 집계하지 않으며 중복되는 이름은 하나로 칩니다.

SELECT COUNT(DISTINCT NAME) FROM ANIMAL_INS 
NOT NAME IS NULL;


## 동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이를 개보다 먼저 조회해주세요.

SELECT ANIMAL_TYPE, COUNT(*) FROM ANIMAL_INS GROUP BY ANIMAL_TYPE ORDER BY ANIMAL_TYPE ASC;

## 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 09:00부터 19:59까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.


SELECT 
HOUR(DATETIME),COUNT(*) 
FROM ANIMAL_OUTS
WHERE HOUR(DATETIME)>=9 AND HOUR(DATETIME)<=19
GROUP BY HOUR(DATETIME) 
ORDER BY HOUR(DATETIME) ASC;


## 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 0시부터 23시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.

SET @HOUR = -1;
SELECT
    (@HOUR := @HOUR + 1) HOUR,
    (SELECT COUNT(*) FROM ANIMAL_OUTS WHERE HOUR(DATETIME) = @HOUR) COUNT
FROM ANIMAL_OUTS
WHERE @HOUR < 23

### SET @HOUR = -1; -> 변수생성
### (@HOUR := @HOUR + 1) HOUR, -> SQL에서는 := 이게 대입연산자임 

## ERROR : Every derived table must have its own alias
### 위와같은 에러는 alias(별명)을 안지어줘서 그럼
EX ) 
SELECT COUNT(NAME)
FROM (
    SELECT NAME
    FROM ANIMAL_INS
    GROUP BY NAME
) A;
여기서 맨 마지막 
) A;줄
) A;


