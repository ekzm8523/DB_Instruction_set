# SQL_Instruction_set
## 검색하기 귀찮아서 한번씩 써본 쿼리문은 여기에 적어놓을것임

## 기초적인 CRUD는 mysql 파일로 들어가면 있음


### DESC [테이블명];
### 테이블의 정보들을 정리해서 보여준다.

### RENAME TABLE [테이블명] TO [바뀔 테이블명];
### 테이블명 변경


![스크린샷 2021-01-13 18 49 09](https://user-images.githubusercontent.com/67869514/104435710-088dc780-55d0-11eb-949a-ec93311909c9.png)


### 3. No transitive dependencies

이중 의존성을 가지면 안된다.

![스크린샷 2021-01-13 18 54 56](https://user-images.githubusercontent.com/67869514/104436352-d761c700-55d0-11eb-9fcb-693459bf6a7f.png)


## 물리적 데이터 모델링
denormalization (역정규화 , 쓰기성능 UP 읽기성능 DOWN)
- 컬럼을 조작해서 join을 줄이기
- 컬럼을 조작해서 계산을 줄이기
- 표를 쪼개기 ( 열을 기준으로, 행을 기준으로 )
- 관계의 역 정규화
등등 여러가지 denormalization이 있다. 역정규화를 하면서 이득과 손해가 있을텐데 저울질을 잘해서 이득인 방법을 적용할것!

index (읽기성능 UP 쓰기성능 DOWN)




테이블에 컬럼추가
ALTER TABLE topic_tag_relation ADD COLUMN tag_name VARCHAR(45) NULL AFTER tag_id;
추가한 컬럼에 컬럼값 추가
UPDATE topic_tag_relation SET tag_name = 'rdb' WHERE (topic_title = 'MySQL') and (tag_id='1');





