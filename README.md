# SQL_Instruction_set
## 검색하기 귀찮아서 한번씩 써본 쿼리문은 여기에 적어놓을것임

## 기초적인 CRUD는 mysql 파일로 들어가면 있음


### DESC [테이블명];
### 테이블의 정보들을 정리해서 보여준다.

### RENAME TABLE [테이블명] TO [바뀔 테이블명];
### 테이블명 변경


# 모델링
## 1. 업무파악  => 2. 개념적 데이터 모델링 => 3. 논리적 데이터 모델링 => 4. 물리적 데이터 모델링

## RDB는 내포관계를 허용하지 않는다.

## 거대 단일 테이블로 표현을 하면 중복이 발생한다.

## 최대한 잘게 쪼개 relation으로 표현하는게 좋다.
잘게 쪼개면 좋은점
1. 자원낭비를 줄일 수 있다.
2. 주제에 따라 groupping을 할 수 있다.
3. JOIN을 사용할 수 있다.


ERD 할때 좋은 서비스
https://app.diagrams.net/

erd.yah.ac

![스크린샷 2021-01-13 14 59 30](https://user-images.githubusercontent.com/67869514/104412608-f2700f00-55af-11eb-80dc-2bc5ece3be2f.png)


![스크린샷 2021-01-13 15 08 11](https://user-images.githubusercontent.com/67869514/104413162-2ac41d00-55b1-11eb-9b6f-9e23d6f7a776.png)


O -> optionality
l -> Mandatory
삼지창 -> 1:N 에서 N

![스크린샷 2021-01-13 16 30 24](https://user-images.githubusercontent.com/67869514/104420042-a5df0080-55bc-11eb-88dc-6d706f406c39.png)


## Normalization (정규화)
### 일반적인 표를 관계형 데이터 베이스에 어울리는 표로 만드는 것
### 최신의 정규화는 훨씬 더 복잡해서 학술적 논문같은데서 많이 다룬다. 우리는 그정도의 정규화는 필요없고 일반적으로 쓰이는 정도의 정규화를 알아볼것이다.

### 1. Atomic columns 


tag컬럼처럼 컬럼값이 여러개라면 Where문으로 찾을때나 정렬할때 애매모호하므로 테이블을 나누는게 1단계

![스크린샷 2021-01-13 18 43 56](https://user-images.githubusercontent.com/67869514/104435101-55bd6980-55cf-11eb-81c2-bc96a16c8f22.png)

### 2. No partial dependencies 

중복키를 없애는게 2단계 부분종속성을 없앤다.

![스크린샷 2021-01-13 18 49 09](https://user-images.githubusercontent.com/67869514/104435710-088dc780-55d0-11eb-949a-ec93311909c9.png)


### 3. No transitive dependencies

이중 의존성을 가지면 안된다.

![스크린샷 2021-01-13 18 54 56](https://user-images.githubusercontent.com/67869514/104436352-d761c700-55d0-11eb-9fcb-693459bf6a7f.png)






