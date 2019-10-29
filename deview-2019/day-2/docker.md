# ms 단위의 Serverless World에서 Docker의 성능 한계 극복하기 [#](https://deview.kr/data/deview/2019/presentation/[213]김동경-ms+단위의+Serverless+World에서+Docker의+성능+한계+극복하기.pdf)
Serverless Computing?
하드웨어 리소스 공유 -> VM 리소스 공유 -> 컨테이너 자체 공유

Backend as a Service
Database as a Service
Function as a Service

Apache OpenWhisk?
* Cold Start
  * 아무것도 없는 상태
  * 컨테이너부터 생성
* Prewarmed Start
  * 컨테이너만 있음
  * 코드 초기화부터 실행
* Warmed Start
  * 코드만 실행
* 스케쥴링 in OpenWhisk?
  * 실행 요청을 어떤 Invoker에게 보낼지 결정
  * 컨테이너의 재사용이 핵심
  * Optimal한 스케쥴링은 불가능
* OpenWhisk의 스케쥴링 방식
  * Hash 함수를 통해 위치 결정
    * 컨테이너 위치 고려 불필요
  * 각 컨트롤러가 리소스를 나누어 가짐
    * Invoker의 리소스 / Controller의 수
    * 리소스가 없으면 머기
    * 다른 컨트롤러의 스케쥴링 고려 불필요
    
근데 도커가 느림
* 도커는 요청을 절차적으로 처리
* 액션간의 간섭
  * 액션 실행 시마다 컨테이너의 생성과 삭제 발생
  * 매번 생성하므로 이후의 모든 실행도 느려짐
  * 해결?
    * 액션 별 메시지 큐를 도입해서 액션 간의 간섭 해결
    * pull 기반 스케쥴링
* 앞선 실행을 기다리지 않음
  * 실행 시간 <= 500ms인 경우, 이전 실행을 기다리는 것이 낫다
  * 해결?
    * 컨테이너의 생성과 액션의 실행을 분리
      * 컨테이너의 생성이 기존 실행에 영향을 주지 않음 (async하게 돌아감)
    * ETCD
      * 주기적으로 리소스 상태 기록
    * Scheduler
      * Kafka를 대체하는 큐를 직접 구현
      * 왜 NO Kafka?
        * kafka는 컨슈머 수와 동일한 수의 파티션 필요
        * 그래서 미리 충분히 만들어 둬야함
        * 컨슈머 개수에 비례한 시간이 걸림
        * 리밸런싱 개발자 결정 불가
      
* 시스템의 성능 결정 불가
  * 동일한 환경에서도 실행되는 액션의 수와 실행하는 유저의 수에 따라 성능이 달라짐
  * 언제 scale-out할지
  * 얼마나 서버를 늘릴지
  * resource planning 불가

