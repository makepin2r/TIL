# 원시값의 메서드, 래퍼 객체 (Wrapper Object)

## 원시값의 메서드
- 모든 원시값은 불변하며 메서드를 내장하고 있지 않음
  - 그러나 어떤 원시값에 대한 메서드를 활용 가능하며, JS에서는 이를 래퍼 객체의 생성을 통해 해결

## 래퍼 객체
- 문자열, 숫자, Boolean 값 등 원시값에 대해 객체처럼 접근하면 생성되는 임시 객체 (== 표준 빌트인 객체)
- 래퍼 객체의 생성자 함수명은 `String`, `Number`, `Boolean` 등 해당 원시 자료형의 이름을 그대로 사용
  - 해당 생성자 함수들은 모두 `[자료형].prototype`의 메서드를 상속

### 래퍼 객체의 생성
1. 마침표 표기법 등 원시값에 객체와 같이 접근했을 때 JS 엔진이 암묵적으로 연관 객체를 생성
  - 해당 객체에 원시값의 자료형에 관련된 연관 프로퍼티 및 메서드가 존재
2. 래퍼 객체 접근이 끝나면 다시 원시값으로 되돌려짐
  - 래퍼 객체는 가비지 컬렉터가 수거

---
#### 레퍼런스
- https://velog.io/@brgndy/%EB%9E%98%ED%8D%BC-%EA%B0%9D%EC%B2%B4Wrapper-Object%EB%9E%80
- https://developer.mozilla.org/ko/docs/Glossary/Primitive
- https://velog.io/@brgndy/%EB%9E%98%ED%8D%BC-%EA%B0%9D%EC%B2%B4Wrapper-Object%EB%9E%80
