# RESTful API

## RESTful API의 정의
HTTP 요청(정보 교환)시 어떤 URI에 어떤 메소드를 사용할지에 대한 약속(형식).
### API 
`Application Programming Interface`의 약자로,
운영체제, 응용 프로그램에서 제공하는 기능을 제어하도록 해주는 인터페이스(제어 장치)
요청과 응답을 연결해주는 것
### REST
자원(문서, 그림, 데이터 등)을 이름으로 구분하여 -> 해당 자원의 상태 및 정보를 주고받는 것

## REST API의 형태
- `URI`와 `HTTP`를 기반으로 한다.
    - (서버는 HTTP 규약에 따라 요청을 전송한다)
- `JSON` 형식을 주로 사용한다. (브라우저 간 호환성이 좋기 때문)
- HTTP 메소드를 활용해 해당 자원에 대한 CRUD를 적용한다
위와 같은 이유로 모든 사람이 URI와 HTTP 메소드의 종류를 보고도 어떤 기능을 하는지 파악이 가능하다.
### URI (Uniform Resource Identifier, 인터넷 식별자)
구조를 통해 자원의 형태를 표현하는 구분자.

## REST API의 특징
- ⭐각 요청이 어떤 동작/정보를 위한 것인지 형태 자체로 추론이 가능해야 한다.
- HTTP 메소드 또한 기능의 목적에 맞게 구분해야 한다. (메소드 자체로 기능 차이가 있는 것이 아님)
    - GET : READ, 데이터를 조회하는 기능
    - POST : CREATE, 데이터를 추가하는 기능. BODY 존재
    - PUT : UPDATE, 데이터를 수정하는 기능. 정보 전체를 수정할 때 주로 사용. BODY 존재
    - DELETE : DELETE, 데이터를 삭제하는 기능.
    - PATCH : UPDATE, 데이터를 수정하는 기능. 정보의 일부만 수정할 때 주로 사용. BODY 존재
    👀 BODY란? 상대적으로 더 많은 정보를 감추어서(안전) 전송 가능하게 함
- URI는 동사가 아닌 명사로만 구성한다.

## 

----
#### 출처
(REST API의 구성)
https://www.youtube.com/watch?v=C7yhysF_wAg
https://www.youtube.com/watch?v=iOueE9AXDQQ
https://www.youtube.com/watch?v=iOueE9AXDQQ
(GraphQL)