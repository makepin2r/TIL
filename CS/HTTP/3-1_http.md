# HTTP
> 인프런 김영한 강사님의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC#)을 학습하고 정리한 내용입니다.

## HTTP (HyperText Transfer Protocol)
- 초반에는 HTML을 전송하기 위한 규약이었으나, 현재는 대부분 모든 것을 HTTP로 전송한다
- 현재 우리가 가장 많이 사용하는 버전은 `HTTP/1.1`(RFC7230~7235)
  - HTTP/2, HTTP/3은 성능 개선

### 기반 프로토콜
- TCP: HTTP/1.1, HTTP/2
- UDP: HTTP/3
- 개발자 도구의 Network 탭을 통해 확인해보자!

### HTTP 특징
- 클라이언트 서버 구조
- stateless 프로토콜, 비연결성
- HTTP 메시지를 통해 통신
- 단순하며 확장 가능

