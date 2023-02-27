# 클라우드 환경 기반 실시간 데이터 처리의 유실 없는 Geo-Replication 구축
김영진, 이모원, 신수인 (NAVER Data Insight Center)

## IDC 장애의 심각성 그리고 Geo Replication
Geo Replication 적용의 3가지 종류
* Performance
* Scalability
* Availability

## Message Queue in Geo-Replication
### Key Elements
* Out-of-the-box feature
  * 개발 난이도와 관리 측면에서 중요
* Synchronous & Asynchronous Replication
  * Synchronous Replication은 데이터 정합정에 강점
  * Asynchronous Replication은 Dynamic Scalability wjrdyd rksmd
* Visible/Measurable Metrics
  * Asynchronous Replication 의 Replication Lag 측정
  * Subscription offset 정보 등의 확인 가능 여부


### Kafka Stretch Cluster
* Synchronous Replication on Kafka
* IDC 간 Network Latency 발생


### Kafka MirrorMaker
* Asynchronous Replication on Kafka
* Active–Active 구성 시, 동일 토픽 간 Multi-named Topic Consuming 필요


### Pulsar Geo Replication
* Synchronous Replication
  * Region Aware Placement Policy
  * Multi-Cluster + 단일 Zookeeper ensemble
  * Multi IDC Data Write Ack
* Asynchronous Replication
  * Rack Aware Placement Policy
  * Write Ack 없이 동작
  * 복제 지연 발생 가능
* Pulsar Automatic Cluster Failover API
  * Primary Cluster의 장애 탐지 시 Secondary Cluster로 자동 전환

## Realtime Data Processing in Geo Replication

### Key Elements
* Cloud Friendliness
  * 장애시 Catch-up reads와 평상시의 Tailing reads 사이의 탄력적 Resource Scaling
  * Cost Efficient 관점에서 중요한 Featu
* Reduced Management with Integrated Processing
  * Message Queue System 과 연결 point를 최소화
  * Fewer Platforms Pipeline이 Geo Replication에 보다 유리
* Data Reusability
  * Data Enrichment 결과 데이터를 얼마나 효과적으로 재사용할 수 있는가?
  * 장애 복구 시 효과적인 리소스 사용


## Cloud Friendliness in Geo Replication

비용 효율적인 Geo Replication 을 위해서는 클라우드 친화 플랫폼이 필요

### Key Elements
* HPA 기반의 Dynamic Resource 할당
  * HPA를 기반으로 한 탄력적 Resource Scaling 을 통해서 빠르게 장애 대응
  * Active/Active, Active/Standby 와 같은 다양한 Resource 구성에 효과적으로 대응
  * Cost Efficient Geo Replication을 위한 필수적 특징
* Modularly Designed Sub-system
  * Monolithic Design 의 경우 Resource 를 효과적으로 Scaling 하기에 불리한 구조
  * Micro Service Architecture 에 유리한 Modular design
* 스케일 인/아웃으로 인한 제약 없음
  * Resource Scaling 으로 성능 저하/기능 제약이 있는 경우 Cloud의 Resource 환경에 부적합

## Efficiently Lossless Realtime Processing in Log-data

## Wrap up
* Cloud
  * Cloud 의 유연한 환경에 기반을 둔 비용 효과적인 Resource 사용
  * HPA에 기반한 시스템 인프라 구축
* Simple
  * 불필요한 데이터 흐름을 최소화한 Platform 구조
  * Single Cluster 내에서의 데이터 처리
* Customized
  * Business Model에 맞는 Tolerant Control
  * Client Level Data Rewind, DB side Deduplication 등 다양한 기술 활용
