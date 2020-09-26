# [Django ORM (QuerySet)구조와 원리 그리고 최적화전략](https://pycon.kr/2020/program/talk/11)

#### Django ORM의 특징
* Lazy Loading
 * 실제로 데이터에 접근하는 시점에 SQL을 호출
 * Greedy하게 호출하기 때문에 2번 호출하게 되는 경우 발생
 * => QuerySet Caching 필요
 * ![](./statics/1.png)
 * 즉시 로딩을 통해 해결
#### QuerySet 상세
* select_related와 prefetch_related
 * selected_related
  * 조인으로 수행
  * => 즉시 로딩
 * prefetch_related
  * 추가 SQL로 수행
  * 전부 새로운 쿼리셋으로 실행
  * => 필드 하나당 쿼리 하나
   => 느린 로딩
 * CaptureQueriesContext 활용 - SQL Performance 커버
### 실수하기 쉬운 QuerySet의 특성들
* prefetch_related와 filter는 완전 별개의 쿼리 실행
 * 메인 쿼리에서 Join하고 추가 쿼리에서 한번 더 조회
 * ![](./3.png)
* annotate => select_related => filter => prefetch_related
 * 이 순서가 실제 SQL 실행 순서와 가장 유사
 * 다른건 몰라도 prefetch_related는 filter 뒤에 두는게 낫다.
* QuerySet 캐시를 재활용하지 못하는 queryset 호출
 * .all을 호출하고 list 문법 사용해서 사용해야
 * ![](./4.png)
* RawQuerySet (.raw) 은 NativeSQL이 아니다
 * 여전히 prefetch_related(), Prefetch() 사용 가능
 * 대신 아래의 내용은 사용 불가
 * ![](./5.png)
* 서브 쿼리 발생 조건
 * QuerySet 안에 QuerySet이 있는 경우에 발생
  * QuerySet이 아니도록 만들어 해결
 * exclude를 역방향 참조 모델에 사용하는 경우에 발생
  * Join으로 풀리게 유도가 불가능
  * prefetch_related(Prefetch())를 사용하는 방식으로 대체
