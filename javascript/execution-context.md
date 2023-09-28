# 실행 컨텍스트
## 실행 컨텍스트
- JS에서 실행할 코드에 제공할 환경 정보들이 모여있는 객체
- 환경 정보들을 모아 컨텍스트를 구성한 뒤 **콜 스택**에 쌓음
- 실행 컨텍스트 내에는 크게 세 가지 정보들이 저장됨
  1. VariableEnvironment
    - 현 컨텍스트 내의 식별자 정보 (environmentRecord)
    - 외부 환경 정보 (outerEnvironmentReference)
    - 실행 시점 LexicalEnvironment의 스냅샷
  2. LexicalEnvironment
    - VariableEnvironment와 동일하나 변경사항이 실시간으로 반영됨
    - 실행 컨텍스트 생성시 VE에 정보가 담긴 뒤 그대로 복사해서 LE를 생성
  3. ThisBinding
    - `this` 식별자가 바라보아야 할 객체
### 실행 컨텍스트 활성화 시점
- 자바스크립트에서 실행 컨텍스트가 활성화되는 시점에 3가지 현상 발생
    1. 호이스팅 발생
    2. 외부 환경 정보 구성
    3. this 값 설정
### 실행 컨텍스트 구성
- 콜스택에 실행 컨텍스트가 쌓이는 시점
    - 전역 공간: 자동으로 구성됨
    - 함수 실행
    - `eval()` 함수 실행
    - block 생성 (ES6+의 경우)

## 렉시컬 환경 (LexicalEnvironment)

---
#### 레퍼런스
- https://junilhwang.github.io/TIL/Javascript/Domain/Execution-Context/
