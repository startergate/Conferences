# 닷넷 17년의 변화 정리 및 닷넷 코어 3.0

CLI 구현체 => CLR<br>
CLS 구현체 => C#, VB.NET

C# 1.0
* 형식 안정성
* Delegate
* Native 코드와의 쉬운 연동

C# 2.0
* 제네릭 지원
  * CLR 의존
* Nullable 지원
  * CLR, .NET BCL 의존
* 부분 클래스 등등 편의성 향상

.NET 3.0/3.5
* 기존 CLR 2.0 + 추가 라이브러리
* WPF
* WCF
* WF(Workflow Foundation)
* WCS (Windows CardSpace)

C# 3.0
* LINQ
  * var 예약어
  * 자동 구현 속성
  * 객체 초기화
  * 컬랙션 초기화
  * 확장 메소드
  * 람다식
  * 등등
  
.NET 4.0
* DLR(동적 언어 런타임) 지원
* 추가 IL 없음, CLR 4.0으로 분리
  * GAC 위치 변경
  * 설치 폴더 변경
  
C# 4.0
* dynamic 예약어 추가
  * Reflection보다 간편한 멤버 접근(public)
  * 동적 언어와의 덕타이핑
  * 동적 언어와의 연동
  

