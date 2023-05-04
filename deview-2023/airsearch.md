# 네이버 검색은 어떻게 나보다 더 내 의도를 잘 아는가?: AiRSearch 반응형 추천
임희재 (NAVER Search)

탐새 과정에서 관심사와 검색의도 구체화

사용자 의도를 예측한 반응형 추천

### 반응형 문제를 풀기 위해서는?
언제/ 어디에서 누구에게?

검색에서 문서를 소비하고 돌아운 사용자들에게

사용자의 행동 기반 정보
* 검색어
* 클릭한 문서
* 사용자의 취향 정보


* Narrow-Down
* Side-By-Side
  * 큰 의도는 벗어나지 않았으나, 범위가 확대됨

검색과 추천의 융합

Intent Query
* 클릭한 문서의 제목에서 핵심 의돌르 표현하는 키워드 찾기
* ColBERT 아키텍처 응용

Intent Walker
* 그래프 기반 사용자 의도에 맞는 문서 추천
  * 클릭 로그 활용 탐색 과정 그래프 생성

User Preference
* 유저의 취향에 적합한 문서를 추천

### 반응형 서비스 개발을 위한 꿀팁
* 문제를 작게 정의하기
  * 빠른 개발
  * 문제 해결의 가능성과 효과 검증
  * 사용자의 피드백으로 문제 확장
* 학습 데이터 잘 구축하기
* A/B 테스트 잘 활용하기
* 지표 모니터링하기