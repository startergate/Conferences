# 모빌리티 데이터팀 신입 분석가의 1년 회고
우리의 이동 방식은 시대와 함께 발전 중

## 데이터로 보는 서울의 이동
* 서울의 아침 인구 이동은 중심 업무 지역으로 주로 이루어짐
  * 주로 업무 지구와 주거 지구는 분리되어 있음
  * but 강남은 두 유형이 혼재되어 있음
* 밤도 유사함
* 파레토의 법칙이 성립
* Origin - Destination Data

## 데이터로 푸는 모빌리티 문제
### ETA 문제
* 차량을 늘린다 => 돈과 시간이 듬. 현실적 문제
* 5분 단위로 반올림을 한다 => 너무 부정확
* 더 정확한 값 제공 => 머신러닝 모델 적용
  * 고객에게 보다 정확한 예상 도착 시간을 보여주자
  * 이탈 막고, 서비스 질 향상
  * 드라이버에 대한 편차가 큼
  * 기본적 정보들 + 드라이버 운행 패턴
  * 고객 경험은 늦게 올 때 나빠짐
  * 늦게 올 때 페널티
* 현실에 모델을 적용할 떄는 다양한 지표들을 함께 고민해야 함
### 차량 운영 효율화
* 노드와 링크
* 현실에서 고려해야할 것
  * 이동 중에 콜이 잡힐 수도
  * 공급은 연속적으로 발생
  
## 회고
* 모델을 만드는 것과 관리하는 것은 차이가 큼
* 상황에 맞는 목적 함수 만들어야 함
  * 필요하다면 손실 함수를 재정의할수도
* 도메인을 머신러닝으로만 분석하지는 말자
* 혼자서 모든 것을 할 수는 없기에
  * 다양한 직군의 사람들과 협업으로 문제 해결
* 주변으로부터 많이 배우기
  * 좋은 사수, 다른 직군의 동료