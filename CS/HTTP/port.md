# PORT
## PORT란
- 같은 ip의 여러 앱과 통신해야 할 때, TCP/IP 패킷 정보 중 TCP 세그먼트에 출발지와 목적지의 포트 번호가 있음
![port](https://github.com/makepin2r/TIL/assets/39889583/692df213-31fc-410b-ae0c-245311188ee1)
  - 0~65535 할당 가능
  - 0~1023는 잘 알려진 포트로 사용하지 않는 것이 좋음
      - FTP: 20, 21
      - TELNET: 23
      - HTTP: 80
      - HTTPS: 443
- IP가 아파트라면 포트 번호는 호수
