# 타다(TADA) 서비스의 데이터 웨어하우스 : 태초부터 한계까지

## init

### Holistics?
* 유료 BI 서비스
* 다양한 데이터 소스 연결
* 다이나믹 필터
* 다른 솔루션들도 많이 있음

### Read Replica
* Aurora MySQL
* 쉽게 리포트 / 대시보드 생성 가능
* 아쉬운 점
  * 새로운 테이블 추가 힘듬
  * SQL 표현력이 아쉬움
  * 여러 소스 Join 불가능
* 혼자 처리하기에는 최선의 선택

## 과도기

### 데이터 웨어하우스
* 데이터를 한 곳으로
  * DB 여러개
  * 스파크로 엮음
* RDS
  * 매니지드여서 쓰기 쉬움
  * 스파크로 write할 때는 upsert가 안됨
  * 그래서
    * 임시 테이블로 write
    * 기존 테이블에 upsert
  * DataFrame의 schema 정보 사용
  * 작업이 멱등적이라서 좋음
  
### 로그 수집
* Kinesis Data Firehose

### 과도기 - 아쉬운 점
* 탄력적 Scale-in/out이 힘듬
* 데이터 웨어하우스로 RDS
  * 새로운 테이블 추가가 용의해짐
  
## 현재
* RDBMS를 매니지드 데이터 웨어하우스로
  * Amazon Athena
    * 서버 로그는 기본적으로 struct
    * Glue Data Catalog 권장 => 테이블/파티션 schema 각각 관리 필요
    * Crawler 가능 => 저거 하는 용도로는 너무함
    * Console 기능 아쉬움 => 과금이 되야만 과금이 얼마나 될 지 알 수 있음
  * Google BigQuery
    * 서버리스, 높은 확장성, 고효율, 데이터 웨어하우스
    * infra 관리 불필요
    * Partitationed Table
      * Date/ Timestamp 형식 가능
      * SQL 성능 향상, batch 작업에 편리
      * Partition을 UPSERT하던걸 partition 단위로 교체
      
### 정리
* 편함, 돈 적게듬
* Firebase 로그가 자동으로

## 결론
* 좋은 데이터 웨어하우스?
  * 풀고자 하는 미션 + 처한 상황에 따라 선택은 달라짐
  * 데이터 웨어하우스들의 장단점 파악하는 능력 중요