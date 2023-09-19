# 비연결성 (Connectionless)
> 인프런 김영한 강사님의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC#)을 학습하고 정리한 내용입니다.

## 비연결성
- HTTP는 기본적으로 연결을 유지하지 않는 모델임
- 일반적으로 초 단위 이하의 빠른 속도로 응답
- 서버 자원을 매우 효율적으로 사용 가능 → 서버 가용성 증가

## 연결-비연결 모델 비교
- 연결 유지 모델 : 서버가 연결을 계속 유지해야 하므로 서버 자원이 낭비됨
  ![image](https://github.com/makepin2r/TIL/assets/39889583/8d7e8261-b89c-4fd5-8657-f97c9b5066a9)
- 비연결 모델 : 응답 완료 후 TCP/IP 연결을 종료 → 최소한의 자원만 유지
  ![image](https://github.com/makepin2r/TIL/assets/39889583/975ccbf8-bc60-4425-89a2-42a0e5790d42)

## 비연결성의 한계 및 극복
### 한계
![image](https://github.com/makepin2r/TIL/assets/39889583/55f38e7d-52c7-49e7-95ae-f2f5dc53eea0)
- TCP/IP 연결을 새로 맺어야 하므로, 3 way handshake 시간이 추가됨
- 웹 브라우저로 사이트 요청시 HTML뿐 아니라 js, css, 이미지 등 수많은 자원이 함께 다운로드됨
### 극복
![image](https://github.com/makepin2r/TIL/assets/39889583/7acc3517-d70d-4dad-bad9-4107807ba6bd)
- HTTP 지속 연결(Persistent Connections)로 문제 해결
  - HTTP/2, HTTP/3 에서 좀더 최적화됨
