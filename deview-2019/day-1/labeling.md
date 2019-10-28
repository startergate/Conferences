# 레이블링 조금 잘못돼도 괜찮아요: Clova가 레이블 노이즈 잡는 법

레이블 노이즈는 모델의 feature extraction을 발생시킴<br>
=> 모델 성능 저하

훈련 모델 = 훈련 방법(데이터, 모델 구조)

해결?
* 모델 구조의 개선
  * 무거운 모델 == 서빙 + 훈련 계산량 증가
* 훈련 방법의 개선
  * 커리큘럼을 만들어 학습
  * 훈련 계산량 증가 + 추가 데이터 필요
* Data Cleaning Method
  * Human Data Cleaning
  * 사람의 도움 없이는?


AutoML
* Split- Train - Check 알고리즘
  * 모든 데이터 검사 불가
* MultiSplit - Train - Check - Vote
  * 다수결
    * 레이블링 히스토리 HMM 모델링
      * 과거의 모든 히스토리를 고려
      * 리소스 소모가 너무 크므로
      * 직전 히스토리만 고려
      
PICO?

* 데이터 품질 전량이 없는 AI 프로젝트는 성공하기 어려움
* AI 데이터 자동 정제 파이프라인은 매우 큰 경쟁력