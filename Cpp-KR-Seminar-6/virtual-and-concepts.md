virtual과 Concepts 비교 - 박동하
-----
Concepts
* Generic Programming 패러다임

타입은 언어 레벨의 개념

타입 시스템? 빠른 오류 발견!

타입 오류 => 연산을 잘못된 값의 집합에 적용

Everything is an object => 추상화하여 문제 표현, 그에 맞게 작성
Class는 이걸 하기 위한 tool일 뿐

추상화 in GP = 재사용 가능한 코드 작성

OOP => 상속 => 제어해야함

GP => 필요에 의한 생성 => 적합한 타입인지 검사

Virtual의 접근법
* 보증
  * 타입 오류 없도록 구현 유도
  * 미래의 코드 생성 제한

Concepts의 접근법
* 확정
  * 코드 생성 전 타입 확인
  * 현재의 코드 생성 제약
* 알고리즘에 맞는 타입
* 타입에 맞는 알고리즘
