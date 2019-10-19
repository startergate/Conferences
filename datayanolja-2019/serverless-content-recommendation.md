#이거 좋아하니? Serverless에서 유저 컨텐츠 추천

유저 기반 추천<br>
콘텐츠 기반 추천

서버리스로?

K-means Clustering?

태그를 기준으로 처리

문제? => Random Centroid
특정한 공간에 집중되어 있으면 부정확한 결과 => K means++

고차원 vector에서 Euclidian distance의 부적절성 => Spherical K-Means<br>
=> confine distance로

문제점? 
* 유저가 API call을 했을 떄만 새롭게 생성해야 함 (항상 돌리고 있으면 낭비)
* 검증에 대한 어려움?
  * 유저들에게는 안 좋을 수 있음
  * 제대로 된 추천이 되었나?
  
Q&A
* K-means는 request 될떄마다 수행. 나머지는 전처리
* 들어온지 얼마 안된 유저들은 추천이 제대로 안되는 경우 => guest 유저 추천 컨텐츠와 조합 