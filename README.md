# SQL_Instruction_set
## 검색하기 귀찮아서 한번씩 써본 쿼리문은 여기에 적어놓을것임

## 기초적인 CRUD는 mysql 파일로 들어가면 있음


### DESC [테이블명];
### 테이블의 정보들을 정리해서 보여준다.

### RENAME TABLE [테이블명] TO [바뀔 테이블명];
### 테이블명 변경


테이블에 컬럼추가
ALTER TABLE topic_tag_relation ADD COLUMN tag_name VARCHAR(45) NULL AFTER tag_id;
추가한 컬럼에 컬럼값 추가
UPDATE topic_tag_relation SET tag_name = 'rdb' WHERE (topic_title = 'MySQL') and (tag_id='1');





