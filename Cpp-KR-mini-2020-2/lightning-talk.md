# 라이트닝 토크

IOCP 예제중에 제로 바이트 리시버를 사용하는 것들이 있는데 이는 램을 절약하기 위한 것으로 메모리가 늘어난 요즘에는 딱히 신경쓰지 않아도 된다. 램이 터져나가는 경우는 거의 없음.

\#include 했을때 그 라이브러리의 모든 걸 가져오는건 C++의 고질적인 문제.\
C++20 부터는 import문 사용. 이를 통해 필요한 것만 불러올 수 있음\
=> 컴파일 시간 감소, 파일 크기 감소, 실행 시간 감소
=> MSVC는 현재 실험 모드에서 사용 가능

std namespace는 모듈화가 잘 되어있음. 근데 모듈화하는거 자체가 어려움

#### C++에서 gRPC 사용
* gRPC는 생산성떄문에 사용 (직접 작성하는 코드가 줄어듬)
* HTTP/2 사용
* Protocol Buffer
  * .proto 파일로부터 직렬화/비직렬화
  * 언어의 제약을 받지 않음
  * Proto3
    * Field를 조합해 Message를 만든다
    * 각 언어에 맞는 타입을 사용해 Getter/Setter가 있는 단위 타입 생성
  * Protocol Buffer Compiler: .proto 파일에서 코드를 생성하는 CLI 도구. 구글 컨벤션 사용하는듯  
* 빌드 도구는 Bazel과 CMake 지원

gRPC 서버 코드 특징
* Server Builder를 사용해 서버를 생성 // builder 패턴
* 동기/비동기 중 1가지만 사용 가능
  * 동기 - virtual member 함수 구현 // callback
  * 비동기 - Completion Queue 사용 // pro-actor 패턴

설치는 vcpkg 쓰는게 제일 쉬움

API 설계는 .proto 파일로 진행/공유