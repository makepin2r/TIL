# TCP, UDP

## 인터넷 프로토콜 스택의 4계층
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/20f6d6a4-572c-464c-964b-019174c59146/036e43ed-01ab-428c-8b89-4bbf31fc00e9/Untitled.png)
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/20f6d6a4-572c-464c-964b-019174c59146/b7604188-74af-4d8d-ad46-1cd8dc133da0/Untitled.png)
(Ethernet frame: 물리적인 하드웨어 정보라고 생각하면 됨)
- IP 패킷에는 출발지, 목적지의 IP 주소가 있다.
    - 패킷 = package + bucket
- TCP 세그먼트: 출발지/목적지의 port 번호, 전송 제어, 순서, 검증 정보 … 가 데이터를 감싸고 있음

## TCP(전송 제어 프로토콜, Transmission Control Protocol)
### TCP의 특징
아래 정보들이 TCP 세그먼트 안에 저장되어있음
- 연결 지향 : TCP 3 way handshake (가상 연결) , 연결을 먼저 하고 메시지 전송
    - TCP 3 way handshake?
        1. SYN (싱크로나이즈) (클라 → 서버)
        2. SYN + ACK (서버 → 클라)
        3. ACK (클라 → 서버) : 함께 데이터 전송 가능하게 최적화됨
        4. 데이터 전송
        - 단, 가상 연결임.
- 데이터 전달 보증: 패킷이 누락되면 알 수 있다.
    1. 데이터 전송
    2. 이후 서버에서 데이터 잘 받았다고 응답
- 순서 보장
    1. 순서가 있는 패킷을 전송
    2. 만일 서버에서 패킷 순서가 잘못되었을 때?
    3. 잘못된 곳부터 순서대로 다시 보내라는 응답을 서버에서 클라로 전송

- 신뢰할 수 있는 프로토콜
- 현재 대부분 TCP 사용중
- 단 데이터 양도 더 많고 비교적 느리다. (최적화가 어렵다.)

## UDP(사용자 데이터그램 프로토콜, User Datagram Protocol)
### UDP의 특징
- 기능이 거의 없다.
    - 3 way handshake 없음 (연결 지향적 X)
    - 데이터 전달 보증 X
    - 순서 보장 X
- PORT + 체크섬(메시지가 맞는지 확인하는 정보)만 추가됨 → 단순하고 빠르다!
    - PORT란?
        - 한 IP에서 여러 앱이 돌아가고 있을 때, 각각 PORT가 있다.
- 애플리케이션에서 추가 작업이 필요하다 (최적화가 가능하다)
- 최근에는 UDP가 각광받고 있다.
    - http3에서는 UDP를 사용중
