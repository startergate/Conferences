# API 설계 우선 방식과 OpenAPI Specification
### 발표자: 신진호 (NHN Cloud)
## API 우선 방식
API-first
* API는 서비스를 성공시키기 위한 전략
Code-First
* API는 기능을 제공하기 위한 전술
## API 설계 우선 방식
API-design-first

API Contract
* API 설계 문서
* 즉, API 설계는 계약
* 계약이 되지 않으면 다음 단계로 진행하지 않음

![](image)
## OpenApi Specification
* 사람과 기계가 읽을 수 있음
* 코드 접근 없이 API 이해 가능
* 언어에 독립적

![](image)

## 시행과 착오

### 용어 통일
* 정리, 분류, 모든 상품에서 만족하는 용어로 통일
### API 설계 문서 관리
* 설계하는 API가 많아지면 문서가 커지고 중복 많이 발생
* 다양한 버전을 나눠서 관리
### 확장
* 프로그래밍 언어에 독립적이기 때문에 특정 언어에만 맞는 기능을 지원하기 어려움
* Extending Templates
  * OpenAPI Generator
  * Mustache
## 사소한 오류
Mock API
* API 설계 운선 방식의 장점 중 하나
