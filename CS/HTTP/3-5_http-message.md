# HTTP 메시지
> 인프런 김영한 강사님의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC#)을 학습하고 정리한 내용입니다.

## HTTP 메시지 구조
![RFC7230 HTTP 메시지 공식 스펙](https://github.com/makepin2r/TIL/assets/39889583/ee2b63d0-d610-4197-90c4-0141d4fef243)
![image](https://github.com/makepin2r/TIL/assets/39889583/2799ef35-2272-4102-960b-7b23a7199ac8)
- start line
- header
- empty line (== CRLF)
- message body (option)
### start line (시작 라인)
#### 요청 메시지
- request-line으로 구성됨
  - 형태: `method` `SP(공백)` `request-target` `SP` `HTTP-version` `CRLF(줄바꿈)`
    - method(http 메서드) : GET, POST, PUT, DELETE... 등 서버가 수행해야 할 동작
    - request-target(요청 대상) : absolute-path[?query]
      - absolute-path(절대경로) : `/`로 시작하는 경로
      - `*`나 http 전체 경로를 다 넣을 수도 있다.
    - HTTP version : HTTP 버전
#### 응답 메시지
- status-line
  - 형태: `HTTP-version` `SP` `status-code` `SP` `reson-phrase` `CRLF`
    - HTTP version
    - status-code(HTTP 상태 코드) : 요청 성공 or 실패 여부
      - 200: 성공
      - 400: 클라이언트 요청 오류
      - 500: 서버 내부 오류
    - reason-phrase(이유 문구) : 상태 코드에 대한 짧은 설명글
### header (HTTP 헤더)
- header-field : `field-name:` `OWS(띄어쓰기 허용)` `field-value` `OWS`
  - field-name: 대소문자 구분 없음
- HTTP 헤더 용도: HTTP 전송에 필요한 모든 부가정보를 담는 것
  - 모든 메타 정보가 다 들어있음
  - 표준 헤더 굉장히 많음!
  - 필요시 임의의 헤더 추가 가능
### message-body(HTTP 메시지 바디)
- 실제 전송할 데이터
- HTML, 이미지, 영상, JSON 등 byte로 표현할 수 있는 모든 데이터 가능
