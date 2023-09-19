# 유사 배열 객체 (Array-like Object)

## 유사 배열 객체의 특징
- 아래의 특징을 갖는 객체
  - 배열과 유사하게 인덱스로 프로퍼티 값에 접근할 수 있음
    - `[]`로 접근할 수 있으나 인덱스는 실제로 key임
    - 객체를 대괄호로 접근할 시 내부의 key를 숫자로 넣더라도 JS가 자동으로 문자열로 변환해 접근함
  - length 프로퍼티를 갖는 객체
    - length라는 프로퍼티를 추가적으로 갖고 있음
- 유사 배열 객체의 실제 형태는 아래와 같다.
  ```javascript
  const arrLike = {
    0: 'a',
    1: 'b',
    2: 'c',
    length: 3
  }
  ```

### 유사 배열 객체와 배열의 차이
- 두 배열의 판별 방법 : `Array.isArray`나 `[array] instanceof Array` 등으로 판단
  ```javascript
  Array.isArray(arrLike); // false
  arrLike instanceof Array // false
  ```
- 유사 배열 객체는 `map`, `filter`, `reduce`, `forEach`와 같은 배열 메서드를 사용할 수 없음
  - `Array.from()`이나 [`Function.prototype.apply()`/`Function.prototype.call()`](https://github.com/makepin2r/TIL/blob/main/javascript/function-method.md)을 사용해야 한다.

- 대표적인 유사 배열 객체
  - 문자열
    - 문자열은 원시 값이나, 원시 값을 객체처럼 사용하면 원시 값을 감싸는 래퍼 객체로 자동 변환된다.
  - `querySelectorAll`이나 `document.body.children`으로 반환된 엘리먼트 리스트

---
#### 레퍼런스
- [MDN Array.from()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
- https://www.zerocho.com/category/JavaScript/post/5af6f9e707d77a001bb579d2
