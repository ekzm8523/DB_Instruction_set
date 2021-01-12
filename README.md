# DB_Instruction_set
## 검색하기 귀찮아서 한번씩 써본 쿼리문은 여기에 적어놓을것임

## 기초적인 CRUD는 mysql 파일로 들어가면 있음


### DESC [테이블명];
### 테이블의 정보들을 정리해서 보여준다.

### RENAME TABLE [테이블명] TO [바뀔 테이블명];
### 테이블명 변경

## JOIN
### JOIN은 RDS를 RDS답게 만드는 명령어이다. 관계를 맺게 해준다.

### mysql> SELECT * FROM author;
![스크린샷 2021-01-12 20 32 52](https://user-images.githubusercontent.com/67869514/104309344-5b567900-5515-11eb-875a-d417db405055.png)

### mysql> SELECT * FROM topic;
![스크린샷 2021-01-12 20 33 08](https://user-images.githubusercontent.com/67869514/104309364-63161d80-5515-11eb-840b-397bb0031bef.png)

### mysql> SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.id;
![스크린샷 2021-01-12 20 33 16](https://user-images.githubusercontent.com/67869514/104309377-68736800-5515-11eb-987a-5efedce34cf1.png)

### mysql> SELECT * FROM [테이블명] LEFT JOIN [다른 테이블명] ON [테이블명].[컬럼명] = [다른 테이블명].[컬럼명];

### 만약 원하는 컬럼만 나오게 하려면
### mysql> SELECT topic.id,title,description,created,name,profile  FROM topic LEFT JOIN author ON topic.author_id = author.id;
![스크린샷 2021-01-12 20 40 39](https://user-images.githubusercontent.com/67869514/104310048-707fd780-5516-11eb-90f3-1d73d6962ef8.png)

### topic.id의 id가 애매하니 이름을 topic_id로 변경해서 출력하려면
### mysql> SELECT topic.id AS topic_id,title,description,created,name,profile  FROM topic LEFT JOIN author ON topic.author_id = author.id;
![스크린샷 2021-01-12 20 40 48](https://user-images.githubusercontent.com/67869514/104310066-75448b80-5516-11eb-90c4-a04c726ff9ed.png)
