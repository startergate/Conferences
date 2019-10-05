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
  
.NET 4.5
* 4.0의 in-place 업데이트 (~ 4.8)
* BCL에 비동기 메소드 추가
* 윈도우 8 스토어 앱 지원
  * .NET for Windows 8.x Store apps (.NET 4.5의 서브셋)
* PCL(Portable Class Library)
  * 대상 플랫폼 설정
  
C# 5.0
* async/await
* BCL에 포함된 호출자 정보 (CallerInfo) 특성 타입
  * 4.0 에서 돌리면 오류가 뜸
    * 직접 만들면 됨
      * Roslyn이 만들어 줌
      
.NET 4.6, .NET Core 1.x
* .NET Standard

C# 6.0
* C# 컴파일러를 닷넷 프레임워크에서 분리
* 간편 표기 구문 추가  

.NET 4.7 ~ 4.8, .NET Core 2.0

C# 7.x
* 튜플 지원 (.NET 4.7 BCL - System.ValueTuple)
* async의 사용자 정의 타입 반환
* 패턴 매칭 지원
* 값 형식의 지원 향상 => 성능 향상
  * 메서드의 매개 변수에 in 변경자 추가
  * readonly 구조체 추가
  * 스택에만 생성할 수 있는 값 타입 및 Span<T>
    * 힙에 생성
    * GC 회피

.NET Core 3.0, C# 8.0
* .NET Standard 2.1
* Windows Form. WPF