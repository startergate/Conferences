# 이미지와 Text정보들을 이용한 쇼핑 카테고리 분류 AI (대규모 분류 문제를 AI로 해결하기) [#](https://deview.kr/data/deview/2019/presentation/[125]이미지와%20Text정보들을%20이용한%20쇼핑카테고리%20분류AI.pdf)
네이버 쇼핑
* 27만개의 스토어
* 10억개의 상품
* 월간 액티브 유저 1600만
* 월간 검색 16억 건

tokenizer를 뭘 쓰든 최종 결과에는 별 차이가 없음

Vocabulary는 적게

이미지 크기가 1/2 수준으로 작아지면 batch size가 약 4배, 속도 약 1/4 수준의 이득

이 경우에서는 224x224가 적당했음

AutoML
* 적은 fcl_dim이 유리
  * fcl_dim?
  
모델 학습 검증
* [SHAP](https://github.com/slundberg/shap)

토크나이저의 튜닝은 학습 데이터에서 오 매칭하기 쉬윈 데이터들을 걸러 내는 것

병렬 Kafka 큐 처리
* 멀티 프로세싱을 통한 전 처리시 CPU 최대 활용
* 10배 성능 개선
* GPU가 Pending되지 않을 만큼의 Throughput을 큐로 관리