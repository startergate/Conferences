# C++를 이용한 Redis 프로그래밍

Redis
* key-value
* Memory db
* 일시적 보존
  * 플레이 상황
* Cache로 사용
* 일부 메인 DB (영구 저장)로도 사용

스레드 모델
* 1 스레드 사용
* 요청 atomic하게 처리

* Expires: 키에 만기 시각 설정

Lua 스크립트 지원

C++ 라이브러리
* hiredis (C 언어용 라이브러리) 사용하여 통신신
  * RedisCpp-hiredis
  * redis_client (기능이 좀 더 많음)
  * r3c (redis 5.0까지 지원)
  * cpp_redis
  * xRedis
* 자체적 통신
  * Boost.Asio 사용
    * redisclient
  * POCO 사용
    * POCO 공식 redis
    * redis-client
    
랭킹 구현 쉽게 가능\
실시간 가능