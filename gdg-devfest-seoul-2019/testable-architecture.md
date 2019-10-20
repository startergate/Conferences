# 테스트 관점으로 아키텍쳐 완성하기 [#](https://speakerdeck.com/maryang/teseuteu-gwanjeomeuro-akitegcyeo-wanseonghagi-testable-architecture?slide=40)
테스트?
* 값이 원하는 형태가 되는가
* 원하는 동작을 연계해서 수행하는가
* 검증하고자 하는 메소드를 수행시켰을 때,
  * 원하는 값의 assert()가 true
  * 원하는 동작의 verify()가 true
  
테스트를 어렵게 하는 것
* 의존 class의 동작
  * Mocking, Stub 활용
* 안드로이드 의존 동작
  * context 기능을 wrapping
  * => wrapping 클래스를 mocking
* => solve => testable architecture

Architecture?
* 코드의 역할을 분리하여 여러 이즘을 얻는다
  * 가독성 (높은 응집도)
  * 변경 유연함 (낮은 결합도)
* MVP, MVVM
* 그냥 사용 시 Not Testable
* 몇 원칙을 기반으로 개선하면 Testable Architecture
  * 의존성 객체는 모두 주입
    * static class를 일반 클래스로 변경
  * 안드로이드 의존 동작은 wrapping
    * SDK => Context 기능 Wrapping
    * UI => View Interface로 Wrapping
    * DB / API => Repository Interface로 Wrapping
    * => MVP의 기본
  * 모든 동작은 Presenter를 사용
    * View는 Presenter 실행만
    * Passive View
    
Instrument Test
* UI Test
* DB Test

Testable Architecture라면 View와 Repository만 추가적으로 테스트

테스트를 어렵게 하는게 저거 2개?<br>
=> x. QA로 하는게 나은거 같다<br>
테스트를 추가할 시간이 없다<br>
효용성을 모르겠다. 너무 바빠서 동기가 안 산다

테스트의 효용성
* 동작 확인
* 변경 유연성 확보
  * 테스트가 있는 class는 변경해도 안심
  * 장기적으로 테스트가 있는게 생산성이 훨씬 빠름
* 코드리뷰를 도움
  * 테스트는 의도를 명시화
  * 테스트를 파악하고 코드를 보면 리뷰가 수월하다
  
테스트 동기부여
* 리포트로 현타를 받자
  * Codecov
* 익숙해질때까지 강제성을 두자
  * 커버리지 이전보다 안 높으면 "Don't Approve"
* 쉬운 것부터 차근차근
  * Presenter/Unit 테스트가
    * 속도가 빠르다
    * 수명도 길다

결론
* 테스트를 잘 하려면 역할이 잘 분리된 Architecture가 필요
* 실제 서비스에서는 영향을 주고받는 컨텍스트가 많음
  * QA는 여전히 필요함
* 복잡하지 않은 동작은 테스트로 검증!