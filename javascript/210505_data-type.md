# 데이터 타입
## 원시 데이터 타입 Orimitive type (기본 데이터 타입)
- 객체가 아닌 데이터 타입
    - 숫자
    - 문자열
    - 불리언
    - null
    - undefined
- 이외의 데이터 타입은 모두 객체이며, **참조 데이터 타입**이라고도 한다.

## 래퍼 객체 Wrapper object
- 래퍼 객체는 원시 데이터를 감싸는 객체이다.
    - 원시 데이터 타입에 필요한 기능을 객체지향적으로 제공해주기 위한 객체
    - 자바스크립트는 내부적으로 래퍼 객체를 자동으로 생성, 제거해준다.
    - `String`, `Number`, `Boolean`은 래퍼 객체이다. 
    - null과 undefined는 래퍼 객체가 없다.

### 래퍼 객체 예시 - String
- 문자열 값에 속성 접근자를 사용해 메소드나 프로퍼티를 사용하려 할 경우, 내부적으로 임시 String 객체가 생성된 뒤 사용이 끝나면 제거된다.
```javascript
var str = 'coding';
// str.length 사용되기 전 str = new String('conding'); 처럼 래퍼 객체가 생성된다.
console.log(str.length); // 6
console.log(str.charAt(0)); // "C"
// 사용이 끝난 래퍼 객체는 내부적으로 소멸된다.
```
```javascript
var str = 'coding';
str.prop = 'everybody'; 
// 위 코드에서 임시로 래퍼 객체가 생성되지만 다시 소멸되므로 undefined 가 출력된다.
console.log(str.prop); // undefined
```