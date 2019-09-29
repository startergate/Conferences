System API와 Coroutine 결합하기 - 박동하
---
서브루틴는 코루틴의 일부분이다?

코루틴
* 호출/종결/중단/재개 가능

구현
* Stackful
  * 스택에 할당
* Stackless
  * 자유 힙 저장소에 할당

* VS2017 ^15.7.13
* Clang ^6
* Appleclang ^10
* GCC 10 Experimental Branch (11?)

구성 요소
* Awaitable
  * 중단 제어
* Promise
  * 코루틴 코드 생성
* handle
  * 구조체와 내장함수로의 인터페이스

분석 포인트
* suspension 
* invoke/return
* 아 뭐였지

뒤는 알아듣기 어려워서 적지 않았습니다

File descriptor? File-like?
