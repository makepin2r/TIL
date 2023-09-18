# URI
> 인프런 김영한 강사님의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC#)을 학습하고 정리한 내용입니다.

## URI (Uniform Resource Identifier)
![image](https://github.com/makepin2r/TIL/assets/39889583/9a6b1077-05c7-42f3-bd3c-7c3a19218293)
- 리소스를 식별하는 방법 중 **URI**가 가장 큰 개념
- 하위에 두 가지가 있음
  ![URL과URN의형태](https://github.com/makepin2r/TIL/assets/39889583/6f924894-e984-4bfe-8d3e-9af34b8a899b)
  - URL (Uniform Resource Locator) : 위치
  - URN (Uniform Resource Name) : 이름

### URI의 정의
- Uniform: 리소스를 식별하는 통일된 방식
- Resource: 자원(=URI로 식별할 수 있는 모든 것), 제한 없음
- Identifier: 다른 항목과 구분하는 데 필요한 정보

**URL의 정의**  
- Locator 즉 리소스가 있는 위치를 지정
- 변할 수 있음
- 대개 URL과 URI를 같은 의미로 사용

**URN의 정의**  
- Name 즉 리소스에 부여된 이름
- URN만으로 실제 리소스를 찾을 수 있는 방법이 보편화되어있지는 않음
- Locator와 달리 변하지 않음
  - ex. urn:isbn:xxxxx (어떤 책의 고유 이름)

## URL의 전체 문법
![image](https://github.com/makepin2r/TIL/assets/39889583/c0d7473c-aa8d-46d4-b078-266f03453f1d)
- **scheme**: 어떤 방식으로 자원에 접근할 것인지에 대한 약속, 규칙
  - 주로 프로토콜이 사용됨
  - ex. http, https(http secure, http에 보안이 추가됨), ftp
  - http는 80포트 https는 443포트를 주로 사용
  - 포트 번호는 생략 가능
- **userinfo**: URL에 사용자정보를 포함해 인증, 거의 사용되지 X
- **host**: 호스트명
  - 도메인명 혹은 IP 주소 직접 사용 가능
- **port** : 접속 포트 번호
  - 일반적으로 생략 가능하며, 생략시 http는 80 https는 443으로 간주
- **path** : 리소스 경로
  - 대개 계층적 구조로 되어있음
- **query**: 웹 서버에 제공하는 파라미터
  - 문자 형태, key=value 형태
  - `?`로 시작, `&`로 추가 가능
  - query parameter, query string으로 부르기도 함
- **fragment**: html 내부 북마크 등에 사용됨
  - 서버에 전송되지 않음
  - 자주 사용되지 않음
