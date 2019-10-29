# 속도의, 속도에 의한, 속도를 위한 몽고DB (네이버 컨텐츠검색과 몽고DB) [#](https://deview.kr/data/deview/2019/presentation/[214]Deview2019_박근배.pdf)
몽고DB index
* 컬렉션 당 최대 64개
* 너무 많이 추가하면...
  * Frequent Swap
  * 쓰기 성능 감소
  * query planner가 엉뚱한 index 선택할 수 있음
* index prefix 사용
* 멀티 소팅
  * sort key 순서 == 인덱스 순서
  * compound index일 때 index key pattern이나 inverse된 pattern과 일치
  
  
* 작은 컬렉션
  * 컬렉션이 너무 커질 경우...
    * 인덱스 사이즈 증가
    * 카디널리티 낮아짐
    * => slow query
* 쓰레드를 사용한 대량의 document upsert
  * 여러개의 thread에서 bulk operation
  * document transaction, a relation 지원 X
* 몽고DB 4.0 사용
  * 몽고DB 4.0 이전은 non-blocking secondary read X
  * 주기적으로 높은 global lock acquire count가 생기고 read 성능 저하
  * 4.0 부터는 data timestamp와 consistent snapshot을 이용해 해결


Query Planner는 이전에 실행한 쿼리 플랜을 캐싱함 (같은 Query Shape인 경우 사용)
