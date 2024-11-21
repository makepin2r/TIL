# 실행 컨텍스트
## 실행 컨텍스트
- JS에서 실행할 코드에 제공할 환경 정보들이 모여있는 객체
- 환경 정보들을 모아 컨텍스트를 구성한 뒤 **콜 스택**에 쌓음
    - 콜 스택은 실행 컨텍스트가 쌓이는 [스택](../Data Structure/stack.md) 형태의 저장소
    - JS는 인터프리터 언어이기 때문에, 스크립트 실행 위치를 추적하는 메커니즘이 필요함. 후입선출 방식으로 실행 순서를 일관되게 보장함
- 실행 컨텍스트 내에는 크게 세 가지 정보들이 저장됨
  1. VariableEnvironment
    - 현 컨텍스트 내의 식별자 정보 (environmentRecord)
      - 컨텍스트 내에서 정의된 식별자(변수), 함수의 매개변수, 선언된 함수들이 저장됨
    - 외부 환경 정보 (outerEnvironmentReference)
      - 실행될 컨텍스트 직전의 실행 컨텍스트가 저장됨.
      - 식별자를 참조할 때 현 컨텍스트 내에 정의부가 없을 경우 외부 컨텍스트를 순차적으로 탐색하며 정의된 곳이 있는지 찾을 수 있음.
      - 호이스팅이 발생! environmentRecord는 모든 식별자 정의에 관한 내용만 모여 저장되고, 값의 할당은 저장되지 않는다. 이로 인해 코드 실행 시 식별자들이 먼저 쭉 정의된 것 같은 현상이 발생하며, 이를 호이스팅이라 표현.
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
- [MDN 호출 스택](https://developer.mozilla.org/ko/docs/Glossary/Call_stack)
- https://junilhwang.github.io/TIL/Javascript/Domain/Execution-Context/
