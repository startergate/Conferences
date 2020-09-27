# [gRPC 프레임워크를 만들며 알아보는 파이썬](https://pycon.kr/2020/program/talk/19)
* gRPC는 프로토콜 버퍼를 사용하기 때문에 XML보다 데어터 처리시 20~100배 빠르고 3~10배 작음
* 서버와 클라이언트 모두 Stub? Proto? 를 공유해야 함

* ProtoBuf는 Swagger처럼 요청과 응답을 명세함
* ![](./8.png)

* ProtoBuf를 컴파일해서 만든 Stub 파일에서 클래스를 상속해서 서비스 구현
### Python gRPC의 불편함
* request 객체의 접근성
 * ListField 직렬화가 불편함
* 중첩된 메시지의 불편함
* 서비스 등록의 복잡함

### Homi?
* 서비스 구현과 서비스 등록을 대신해줌
* 플라스크와 유사한 인터페이스 제공
* 자동 시리얼라이제이션
