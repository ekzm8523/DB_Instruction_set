
## JOIN
### JOIN은 RDS를 RDS답게 만드는 명령어이다. 관계를 맺게 해준다.
##https://sql-joins.leopard.in.ua

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

mysql> CREATE TABLE author ( aid int(11) NOT NULL, name varchar(10) DEFAULT NULL, city varchar(10) DEFAULT NULL, profile_id int(11) DEFAULT NULL, PRIMARY KEY (aid))ENGINE=InnoDB DEFAULT CHARSET=utf8;

mysql> INSERT INTO author VALUES (1,'jaewon','seoul',1),(2,'jaetwo','deokso',2),(3,'jaethree','incheon',3);
              
mysql> CREATE TABLE profile ( pid int(11) NOT NULL, title varchar(10) DEFAULT NULL, description tinytext, PRIMARY KEY (pid) )ENGINE=InnoDB DEFAULT CHARSET=utf8;
mysql> INSERT INTO profile VALUES (1,'developer','developer is...'),(2,'designer','designer is ...'),(3,'DBA','DBA is...');

mysql> CREATE TABLE topic( tid int(11) NOT NULL, title varchar(45) DEFAULT NULL, description tinytext, author_id varchar(45) DEFAULT NULL, PRIMARY KEY (tid) )ENGINE=innoDB DEFAULT CHARSET=utf8;
mysql> INSERT INTO topic VALUES (1,'HTML','HTML is ...', '1'),(2, 'CSS', 'CSS is ...', '2'),(3, 'JavaScript', 'JavaScript is ...', '1'),(4, 'Oracle', 'Oracle id ...',NULL);

![스크린샷 2021-01-13 13 43 15](https://user-images.githubusercontent.com/67869514/104407590-4c1f0c00-55a5-11eb-8862-be02752bc441.png)


# LEFT JOIN ( A + A ∩ B )

mysql> SELECT * FROM topic LEFT JOIN author ON topic.author_id=author.aid;

![스크린샷 2021-01-13 14 14 49](https://user-images.githubusercontent.com/67869514/104409469-b3d75600-55a9-11eb-88af-e76cab98cb9a.png)

mysql> SELECT * FROM topic LEFT JOIN author ON topic.author_id=author.aid LEFT JOIN profile ON author.profile_id=profile.pid;

![스크린샷 2021-01-13 14 14 35](https://user-images.githubusercontent.com/67869514/104409454-ab7f1b00-55a9-11eb-8dc4-bb1e5d4ab2c4.png)

mysql> SELECT tid,topic.title,author_id,name,profile.title as jobtitle FROM topic LEFT JOIN author ON topic.author_id=author.aid LEFT JOIN profile ON author.profile_id=profile.pid;

![스크린샷 2021-01-13 14 15 16](https://user-images.githubusercontent.com/67869514/104409505-c3ef3580-55a9-11eb-8fa7-307f0d35a539.png)

mysql> SELECT tid,topic.title,author_id,name,profile.title as jobtitle FROM topic LEFT JOIN author ON topic.author_id=author.aid LEFT JOIN profile ON author.profile_id=profile.pid WHERE aid=1;

![스크린샷 2021-01-13 14 15 27](https://user-images.githubusercontent.com/67869514/104409517-c9e51680-55a9-11eb-9b9a-26df93fe6560.png)


# INNER JOIN
## Inner Join은 LEFT JOIN , RIGHT JOIN 보다 조금 더 엄격해서 NULL값으로 되어있는 relation은 가져오지 않는다. ( A ∩ B )

mysql> SELECT * FROM topic LEFT JOIN author ON topic.author_id=author.aid INNER JOIN profile ON author.profile_id=profile.pid;

![스크린샷 2021-01-13 14 24 46](https://user-images.githubusercontent.com/67869514/104410148-18df7b80-55ab-11eb-9a63-590db35197a0.png)

# FULL OUTER JOIN (A u B)
## FULL OUTER JOIN 은 합집합이고 LEFT JOIN + RIGHT JOIN 후 중복 제거를 한것인데 잘 쓰이지 않음 많은 DB에서 지원하지 않는 모델

# EXCLUSIVE JOIN
## A - (A ∩ B) 이것도 웬만하면 쓰지 않을듯...? 필요할떄 검색 ㄱㄱ

![스크린샷 2021-01-13 14 37 51](https://user-images.githubusercontent.com/67869514/104411020-edf62700-55ac-11eb-9fa7-84a6c753a1d1.png)





