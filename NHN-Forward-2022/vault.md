# 실전 Vault 도입기
* Kerberos
  * MIT
  * 단일 서버 구성
  * 티켓 기반 네트워크 인증
  * 클라이언트로 동작
* Vault
  * HashiCorp
  * 클러스터
  * API


* 시크릿 저장소
  * 동적 시크릿
  * 정적 시크릿
* 데이터 암호화
* ID 기반 접근
* 키 관리

![](image)

여러명이 키를 입력해야 unseal 되도록 설정할 수 있음

실행 환경
* 패키지 매니저
* 바이너리 파일
* 소스 파일 설치
* Helm
* Docker 이미지
* HashiCorp Cloud Platform

다양한 사용자 인증 방식 제공

## CA
다수의 개발 툴에서 개인 키 인증 기능을 지원하지 않았음

## One Time Password

## 클러스터
로드 밸런서를 사용한 클러스터

High Availability 클러스터
* 1 leader : N followers 구성
* 통합 저장소로 고가용성 스토리지 구현
  * Raft Storage

## 그 외
* MySQL 계정 다이나믹하게 생성하기
* 그라파나에서 모니터링 하기
* 계정 정보 암호화 하기
* 등..

## 후기
* 툴마다 OTP를 쓸 때, 툴마다 연결 방식이 달라서 매번 비밀번호를 요청하기도 함
* 클러스터 구성 후, Vault 노드 절반 이상이 다운되면 멀쩡한 노드도 다운됨
* Vault는 APi 접근 정책만 관리하고 사용자 관리는 다른데서 해야 함
