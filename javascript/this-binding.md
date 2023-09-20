# this 바인딩
- JS에서 this는 함수가 어떻게 호출되었는가에 따라 동적으로 결정된다.
  - 일반적인 함수 호출
  - 메서드 호출
  - 생성자 함수 호출
  - Function.prototype.apply/call/bind 에 의한 간접 호출
## 1. 일반 함수 호출
- 일반 함수 호출시 기본적으로 전역 객체(global object)가 바인딩됨
  - this는 객체에서 프로퍼티나 메서드를 참조하기 위한 자기 참조 변수이므로
  - 일반 함수는 객체를 생성하지 않기 때문임
```javascript
function foo() {
  console.log("foo", this);
  function bar() {
    console.log("bar", this); 
  }
  bar(); // window
}
foo(); // window
```
- 단 `strict mode`가 적용된 일반 함수의 경우 `undefined`가 바인딩됨
```javascript
function foo(){
  'use strict';
  console.log("foo", this);
  function bar() {
    console.log("bar", this); 
  }
  bar(); // undefined
}
foo(); // undefined
```
### 콜백 함수/중첩 함수
- 콜백 함수/메서드 내에 정의된 중첩 함수도 일반 함수로 호출시 전역 객체가 바인딩된다.
```javascript
// 중첩 함수 예시
var value = 1; // var로 선언했으므로 전역 객체의 프로퍼티

const obj = {
  value: 100,
  foo() {
    console.log("foo", this); // {value: 100, foo: f}
    console.log("foo", this.value); // 100

    // 중첩 함수
    function bar() {
      console.log("bar", this); // window
      console.log("bar", this.value); // 1
    }
    bar(); // 일반 함수로 호출되었으므로 전역 객체가 바인딩됨
  }
}

obj.foo();
```
```javascript
// 콜백 함수 예시
var value = 1;

const obj = {
  value: 100,
  foo() {
    console.log("foo", this); // {value: 100, foo: f}

    // 콜백 함수, 전역 객체가 바인딩
    setTimeout(function(){
      console.log("callback", this); // window
      console.log("callback", this.value); // 1
    }, 100);
  }
}

obj.foo();
```
**메서드의 this와 중첩/콜백 함수의 this를 일치하기 위한 방법**
1. 내부에서 this를 재할당
   ```javascript
     const obj = {
       value: 100,
       foo() {
         const that = this; // 현재 객체의 this를 할당
         setTimeout(function(){
           // this 대신 
            console.log("callback", that.value); // 100
          }, 100);
       }
     }
   ```
2. [Function.prototype.apply/call/bind](https://github.com/makepin2r/TIL/blob/main/javascript/function-method.md) 활용

## 2. 메서드 호출
- 메서드에는 메서드를 호출한 객체가 this로 바인딩됨
  - 주의: 메서드를 소유한 객체 X 메서드를 호출한 객체 O
  - 즉 마침표 연산자 `.` 앞의 객체가 this가 됨
```javascript
const person = {
  name: 'Lee',
  getName() {
    return this.name;
  }
}

const anotherPerson = {
  name: 'Kim'
}

anotherPerson.getName = person.getName; // 다른 객체의 메서드를 할당받음
console.log(anotherPerson.getName()); // Kim

const getName = person.getName;

// 일반 함수로 호출시 전역 객체가 바인딩되므로 name이 없다.
console.log(getName()); // ''
```
- 프로토타입 메서드 또한 메서드를 호출한 객체가 this에 바인딩됨
  - 프로토타입 또한 객체이며 직접 메서드를 호출할 수 있기 때문
```javascript
function Person(name){
  this.name = name;
}

Person.prototype.getName = function () {
  return this.name;
}

const me = new Person('Lee');
console.log(me.getName()); // Lee

Person.prototype.name = 'Kim';
console.log(person.prototype.getName()); // Kim
```

## 3. 생성자 함수 호출
- 생성자 함수의 경우 생성자 함수가 미래에 인스턴스화될 때 해당 인스턴스가 this로 바인딩됨
  - 생성자 함수 == 객체(인스턴스)를 생성하는 함수
  - `new` 연산자와 함께 호출할 경우 생성자로 동작하며, new 연산자를 사용하지 않으면 일반 함수로 동작함
 
## 4. Function.prototype.call/apply/bind 에 의한 간접 호출
- `call`, `apply`, `bind`를 활용하면 직접 인수로 전달받은 객체를 명시적으로 this를 할당해줄 수 있다.
- [링크 참고](https://github.com/makepin2r/TIL/blob/main/javascript/function-method.md)

---
#### 레퍼런스
- <모던 자바스크립트 Deep Dive>
- [MDN this](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)
