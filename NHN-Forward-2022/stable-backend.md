# 편안한 휴식 시간을 지켜줄 안정적인 백엔드 운영과 개발 기법
### 발표자: 정재범 (NHN Dooray)

개발 담당자가 서비스를 직접 운영

장점
* 빠른 장애 대응
* 최적의 서버 구성
* 설계/개발 단계에서 운영 고려

단점
* 불안
* 피로
* 비 전문성

## 자동 재시작
재시작이 필요한 경우
* GC death spiral
  * ![](image)
  * 제한이 없는 요청 응답 레코드 수
  * 해제되지 않는 객체 참조
* 스레드 차단이 필요한 경우
* 데드락

bash와 크론탭으로 프로세스 살아있는지 자동 재시작 구성

하지만 JVM은 OOM 오류에도 죽지 않음

JVM 실행 옵션에는 ExitOnOutOfMemory 옵션이 있음

-XX:OnOutOFMemoryError='script'

쿠버네티스의 LivenessProbe
* ![](image)

효과
* 일시적인 장애는 익일 확인 후 대응 가능
* 무중단 서비스 유지

위험 관리
* 위험 대응
  * 정지 -> 생각 -> 호흡 -> 행동
  * 성급한 대응은 상황을 악화시킴
* 자동화
  * 반복된 패턴은 자동화 지향

## 과도한 부하를 견디는 방법

cascading failure
* 소수 서버의 문제가 다른 서버의 문제로 이어지며 이슈가 점진적으로 연결된 서버에 오류 유발
* 원인
  * 일부 서버 과부하
  * 자원 부족
  * 서버 crash

지표의 측정
* Spring Boot의 Actuator 활용
  * Metric과 Prometheus Endpoint
* Grafana 연동
* 측정 항목
  * CPU 사용률 
  * 액티브 스레드

대응 방안
* Scale in/out
  * 리소스 사용량이 최번시에 급증
  * 최번시 사용량을 위한 리소스를 항상 확보하기엔 비용 이슈
* Message Broker로 지연 처리
* IaaS, K8s Auto Scale
  * 단기간에 폭증하는 요청을 Auto Scale이 커버할수 없다
* 서킷 브레이커 패턴
  * 이미 서버에 부하가 발생한 후 동작
  * 장애가 일시적으로 사용자에게 노출
  * 간헐적인 오류가 지속 노출
* 429 - Too Many Request
  * 사용자 인터렉션이 없는 API
  * 기준
    * 초당 요청량
      * 구현이 쉬움
      * 서버의 처리량을 일정하게 제한
    * CPU 사용량
      * 연계 서버의 응답 지연으로 백엔드 시스템에서 병목이 발생하는 경우 Cascade Failure 유발
    * Active Thread 수
      * Spring Boot Actuator의 MetricsEndpoint 활용
      * ![](image)

## 백엔드에서 HTTP Cache 활용
* Cache-Control: must-revalidate
* ETag 헤더
  * 응답하는 리소스의 버전을 제공
* If-None-Match 헤더
  * HTTP 요청을 조건에 따라 응답 가능
  * 클라이언트가 ETag를 If-None-Match 헤더에 포함
  * ETag를 비교하여 다른 경우에만 응답

Apache HttpClient-Cache의 Storage Backend
* in-memory
* EhCache
![](image)
![](image)

주의사항
* Shared Cache 주의
  * 기본 설정: public인 경우에만 cache
  * API의 URL 외 인증 등 기타 정보로 데이터가 변경될 경우 사용하면 큰일남
* Method
  * HTTP Cache는 GET에서만 적용됨
* Storage Backend

## Netty 소켓 서버
request 크기는 작은데 response 크기가 매우 큼

Channel.isWritable() 사용
* 클라이언트 네트워크 상태가 괜찮은가

* 지속적인 작업
* 가시화
* 아이디어
  * 반복작업 자동화
  * RFC, W3C 문서에 보석이 숨어있음
