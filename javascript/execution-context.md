# 실행 컨텍스트
## 실행 컨텍스트 (이후 추가 학습 예정)
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
## 렉시컬 환경 (LexicalEnvironment)
