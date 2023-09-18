# 웹 브라우저 요청 흐름
> 인프런 김영한 강사님의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC#)을 학습하고 정리한 내용입니다.

## 브라우저 → 서버 흐름
-  웹 브라우저에서 아래의 일들을 수행
  ![image](https://github.com/makepin2r/TIL/assets/39889583/5173a8ac-20e5-4bce-a254-42ac05808717)
  1) DNS 조회 → IP 주소 확인
  2) 포트 번호 확인 (생략시 프로토콜에 따라 자동 부여)
  3) HTTP 요청 메시지 생성 (데이터 요청 방식, path, HTTP 버전 정보, Host 정보)
     ![image](https://github.com/makepin2r/TIL/assets/39889583/b6aa41fe-2702-4de0-b78d-6e7e552ec557)
- 패킷 생성
  ![image](https://github.com/makepin2r/TIL/assets/39889583/ed9591e4-03d2-4d33-8e6f-539a1e8d3ce4)
  - 브라우저에서 생성한 HTTP 메시지가 패킷에 전송 데이터로 포함됨
- 서버로 전송

## 서버 → 브라우저 흐름
- 패킷 내의 데이터를 읽고 HTTP 응답 메시지 생성 (HTTP 버전 정보 및 status, Content-Type, Content-Length, 내용)
  ![image](https://github.com/makepin2r/TIL/assets/39889583/5a19435e-7d19-4a81-b472-e11dc6120921)
- 브라우저와 동일하게 TCP 패킷 생성하여 인터넷망 통해 전송
- 브라우저는 HTTP 응답 메시지를 통해 전달 받은 HTML을 렌더링
