# K8s 도입하면서 겪은 일들
### 발표자: 정재범 (NHN Dooray)

## 도입 배경과 배포
* pod
  * 프로세스를 실행하기 위한 가장 작은 단위
* service
  * pod를 묶어줌
* node
  * 피지컬 리소스
* ingress
  * 엔드포인트
* deployment
  * 배포 단위
## 도입 후 장단점
장점
* 설치 없음
* 배포의 편리함
  * 기존
    * 여러개의 터미널
    * 롤백에 대한 스트레스
* 셀프 힐링
단점
* 새로운 개념
## Pod와 Deployment
* 노드가 먹통이 됨
  * Pod에 최대 사용량 지정
* 코드가 달라고 yaml이 다르지 않으면 변경사항이 반영되지 않을 수 있음
* 내 Pod가 배치 작업에 영향을 받음
  * nodeAffinity로 해결
* 내 Pod가 한 노드에만 배포됨
  * podAntiAffifity로 골고래 배치되도록 설정 가능
## Ingress
* ACL 문제
* 포트가 기억이 안 나는 문제
## Liveness Probe와 Readiness Probe
Liveness Probe
* Pod는 살아있는데 애플리케이션 서비스가 비정상인 경우
Readiness Probe
* 재배포 시 순단 발생
  * 준비 상태 검사
## K8s 운영 꿀팁
* Pod 꿀팁
  * -o wide - 어떤 노드에 올라가 있는지
* 로그 꿀팁
  * stern
  * 로그 관리 시스템 필요
