# 월간 GDG: 광주 12월호 (2019)
### 레이블링 조금 잘못돼도 괜찮아요

레이블 노이즈가 늘어나면 불필요한 패턴을 학습하게 됨\
=> Feature Extraction 어려워짐 => 모델 성능 저하

훈렴 모델 = 훈련방법(데이터, 모델 구조)

복잡한 패턴도 잘 인식하는 모델 구조 사용\
=> 모델이 무거워짐 => 서빙+훈련 계산량 증가

커리큘럼 러닝?\
=> 커리큘럼을 만드는 모듈 추가, 또 하나의 모델을 구상하기도 함(MentorNet)\
=> 훈련 계산량 증가 + 추가 데이터 필요

데이터셋 자체를 clean\
=> Active Learning\
=> ReLabeling을 기계가 스스로 하면 어떨까?

### 레이블링 바로잡는 AutoML
Split - Train - Check
* Split
  * 데이터셋을 train / valid set으로 분할
* Train
  * checker: 레이블 Correction 용도로 훈련된 모델
  * train set으로 checker를 훈련
* Check
  * valid set을 훈련된 checker에 입력하여 labeling 검

=> 모든 데이터를 검사할 수 없

MultiSplit - Train - Check - Vote
* MultiSplit: 여러 버전의 split branch 구성
* Vote: Label Update를 위해 각 branch의 split-train-check 결과 결합

PICO Vote?\
반복적 확률적 Vote를 통해서 점진적으로 레이블 노이즈 제거

직전 state의 정보만 반영