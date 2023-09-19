# 클라이언트 서버 구조
> 인프런 김영한 강사님의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC#)을 학습하고 정리한 내용입니다.

## 클라이언트-서버 구조
![image](https://github.com/makepin2r/TIL/assets/39889583/f34d83f0-56ed-40b2-a336-c4fbbdf116f8)
- Request-Response 구조
  - 클라이언트 → 서버 : 요청을 보내고, 응답 대기
  - 서버 → 클라이언트 : 요청에 대한 결과를 만들어 클라이언트에 응답
- 클라이언트와 서버를 분리하는 자체가 중요. → 클라이언트/서버가 독립적으로 진화 가능
  - 서버: 비즈니스 로직 및 데이터 일임
  - 클라이언트 : UI 및 사용성 일임

