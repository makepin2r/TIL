# 자바스크립트 생성자

## 생성자
- `new` 연산자와 함께 생성자 함수를 호출하면 객체(인스턴스)가 생성된다.
- 기본 객체 형태의 Object 및 String, Number, Boolean, Function, Array, Date, RegExp, Promise 등 빌트인 생성자 함수가 내장되어있음
- 생성하고자 하는 프로퍼티 구조가 같을 경우, 직접 생성자 함수를 작성해 템플릿화할 수 있다.

### 생성자 함수
- 객체(인스턴스)를 생성하는 함수
- JS에서는 클래스 기반 객체지향 언어와 달리 일반 함수와 동일하게 정의한 함수를 `new`와 함께 호출하는 방식을 사용한다.
  - `new` 연산자와 호출하지 않으면 일반 함수처럼 동작
  - `new` 연산자를 사용하면 JS 엔진이 암묵적으로 인스턴스 생성 및 반환을 수행
```javascript
function Circle(radius) {
  // 1. 암묵적으로 인스턴스 생성된 뒤 this에 바인딩됨 (런타임 이전에 실행됨)
  // 2. 인스턴스 초기화 과정
  this.radius = radius; 
  this.getDiameter = function () {
    return 2 * this.radius;
  };
  // 3. 초기화된 인스턴스가 바인딩된 this가 암묵적으로 반환됨
}

const circle1 = new Circle(5); // 객체가 생성됨
const circle2 = Circle(10); // 반환문이 없어 리턴되는 것이 없음

console.log(circle1.getDiameter()); // 10
console.log(circle2); // undefined
console.log(radius); // 5. 일반 함수로서 호출되었으므로 Circle 내의 this가 전역 객체를 가리키게 됨

// 출처: <모던 자바스크립트 Deep Dive>
```
- 생성자 함수는 암묵적으로 생성된 인스턴스가 바인딩된 this를 반환한다. 그러나 명시적으로 반환문을 작성할 경우 두 가지로 작동한다.
  1. this가 아닌 다른 객체를 명시적으로 반환하면 this의 반환이 무시됨 (return문에 명시한 객체를 반환)
  2. 원시 값을 명시적으로 반환하면 원시 값의 반환이 무시됨 (this를 반환)
  → 생성자 함수에서 return 문 명시는 지양할 것
- 생성자 함수는 두 가지 역할을 수행
  1. 인스턴스 생성
  2. 생성된 인스턴스 내의 프로퍼티 초기화 (옵션)

---
**레퍼런스**
- <모던 자바스크립트 Deep Dive>
- https://koocci-dev.tistory.com/56
- https://www.zerocho.com/category/JavaScript/post/573c2acf91575c17008ad2fc
     
