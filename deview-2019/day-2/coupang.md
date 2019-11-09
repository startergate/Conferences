# 쿠팡 추천 시스템 2년간의 변천사 (상품추천에서 실시간 개인화로) [#](https://deview.kr/data/deview/2019/presentation/[215]%20쿠팡추천시스템%20변천사%20(배포용).pdf)
모델 중심의 아키텍처
* 모델 변경에 따라 길어지는 파이프라인
* 추가 요청 사항 처리 어려움
* 완성 전까지 결과 알기 어려움
* 개발 시간 오래 걸림
* 점진적 개선 어려움
* 모델 재활용 어려움

FIX!
* 추천 모델과 서비스 분리
* 상품 정보나 유저 정보를 서빙 타임에 접근 가능하게
* 필터, 부스팅 등의 변경이 쉽고 빠를 것

Protocol Buffer
* gRPC
* 빠른 시리얼리제이션
* 암축 효율
* 스키마 변경
* 태그 넘버
* Null X
* HIVE X

모델과 서비스의 분리
* 서비스는 있는 피쳐를 어떻게 쓸지 고민
  * 지속적 쿼리 튜닝
* 모델은 좋은 피쳐를 만들기 위해 노력
  * 만들어진 피처는 다른 서비스에도 사용


그래서...
* 빠른 서비스 개발
* 비즈니스

쿼리 튜닝을 모델에게...
* Search Cluster
  * 각 노드는 모델을 들고 각자의 추천 후보 상품 리랭킹
* Training
  * 실시간 로깅
  * 새로운 피처는 쿼리를 재현하여 crawl
  * 유저 피드백 backfill
  
개인화
* 실시간 사용자 피처
  * 실시간 로그 => Redis
* 모든 피처를 갖다 쓰면
  * 성능이 더 좋을 순 잇음