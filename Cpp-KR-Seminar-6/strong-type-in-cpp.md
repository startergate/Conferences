Strong Type
----------
Strong type?
* Tag Dispatch, Builder/Factory 패턴 => Over Abstraction
* 새로운 타입 만들기
* 적절한 추상화를 위해 사용

Why?
* Type Safety
* 가독성
* Generic Programming
* Testability
  * 함수를 total하게 함
* Reusability
* staric polymorphism

Algebraic Data type
* 일종의 composite type
* sum type
  * optional
  * variant
* Product type
  * tuple
* List type
  * vector

단점
* 설계할 타입이 너무 많음
* 생성자가 너무 많아
  * 이동, 복사 생성자 직접 구현해야
* 디버깅 어려움
* 라이브러리 문제들
* 최적화 문제

결론
* 어떻게 타입 디자인?
  * Over Abstraction Under Abstraction 사이의 어딘가
  * 타입을 더 낫게 설계
