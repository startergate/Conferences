# 네이버 스케일로 카프카 컨슈머 사용하기
이동진 (NAVER Platform Labs)

### Kafka
* Topic
  * 1개 이상의 Partition으로 분할, 1개 이상의 Replica로 복제된 Log 자료 구조
* Client
  * Producer: 쓰고자 하는 Topic Partition의 맨 끝에 record를 추가
  * Consumer: 읽어오고자 하는 Topic의 Partition에 저장된 record를 순차적으로 읽어옴


* Consumer Group
  * 같은 group.id 설정 값을 가진 Consumer들은 하나의 Consumer Group을 이룬다
  * 같은 Consumer Group에 속한 Consumer들이 Topic에 속한 Partition들을 나눠서 읽는다
  * Consumer Group == "논리적인 Comsumer"
  * 거대한 Consumer 하나가 전체 Topic 내용을 읽어들이는 것 처럼 보인다
  * 제대로 동작하기 위해 필요한 것은?
    * 중복도 누락도 없이 할당해주는 매커니즘 (Partition Assignment)
    * 어디서부터 작업을 시작하면 되는지 저장하고 불러오는 매커니즘 (Offset Commit)


* Consumer Coordination
  * Comsumer Group Coordinator
    * Consumer Group에 변경이 생겼는지 탐지
    * TopicPartition에 변경이 생겼는지 탐지
    * Comsumer Group Leader와 나머지 Comsumer들간의 Communication 중개
  * Consumer Group Leader
    * 현재 구독중인 topic의 파티션들을 consumer들에 할당
  * Broker를 재시작할 필요 없이 더 유연하고 확장 가능한 파티션 할당을 지원하기 위해

### Cloud 환경에서의 Consumer Group Coordination
* group.instance.id
  * 정적 그룹 멤버십
  * 정상적 재시작 이전에 할당되어 있던 파티션들을 다시 할당
  * 단순 pod 재시작 때문에 Partition Rebalance가 발생하는 사태를 방지
* session.timeout.ms
  * Consumer 프로세스가 Broker가 신호를 주고받지 않고도 리밸런스를 생성시키지 않는 최소 시간
* broker.rack
  * Failover Replica로부터 읽기
  * 클라우드 시대로 넘어오면서 의미 변화
    * 물리적 서버 랙 -> 가용 영역
    * Consumer와 Leader Replica가 서로 다른 가용 영역에 있으면?
      * Consumer가 위치한 AZ를 알고 있고, 해당 AZ에 leader replica와 동기화된 상태를 유지고하 있는 follower replica가 있으면 거기서 가져오자

### 네이버 스케일
* 본질적인 원인
  * Rack이 가리키는 바가 지나치게 애매모호 하다
  * Partition Assigner가 rack 정보를 고려하지 않는다
* 기존 Consumer Protocl=p
