# Function.prototype의 메서드
- `Function.prototype`의 메서드는 모든 함수가 상속받아 사용할 수 있다.
- 대표적인 메서드: `apply`, `call`, `bind`

## Function.prototype.apply(), Function.prototype.call()
- 본질적 역할 : 함수의 호출
  - 함수 호출시 첫 번째 인자로 들어오는 객체를 호출한 함수의 this에 바인딩
- 두 개의 인자를 받음
    1. this로 사용할 객체
    2. 인수 리스트
         - `apply` : 배열 또는 [유사 배열 객체](https://github.com/makepin2r/TIL/blob/main/javascript/array-like-object.md)
         - `call` : 인수를 하나씩 받는다.
```javascript
//Function.prototype.apply(thisArg[, argsArray])
//Function.prototype.call(thisArg[, args1[, args2[, ...]])

const getThisBinding = () => {
  return this;
}
const thisArg = { a : 1 }; // this로 사용될 객체

console.log(getThisBinding.apply(thisArg)); // { a : 1 }
console.log(getThisBinding.call(thisArg)); // { a : 1 }
console.log(getThisBinding()); // window

getThisBinding.prototype.apply(thisArg, [1, 2, 3]);
getThisBinding.prototype.call(thisArg, 1, 2, 3); 
```
### 자주 쓰이는 용법
- 유사 배열 객체에 배열 메서드를 사용할 때
  - 유사 배열 객체는 배열의 메서드를 사용할 수 없으므로 `apply`나 `call`을 이용해 해당 메서드를 사용할 수 있다.

## Function.prototype.bind()
- 본질적 역할 : 함수의 this를 교체
  - 첫 번째 인자로 전달된 객체를 함수의 this에 교체해 바인딩한 뒤 리턴
- `bind` 자체로 함수를 호출하지 않으므로, bind된 함수를 실행하려면 명시적인 호출이 필요
```javascript
getThisBinding.bind(thisArg); // thisArg로 this가 바인딩된 새로운 getThisBinding 함수를 반환
getThisBinding.bind(thisArg)(); // 실행하려면 명시적인 호출 필요
```
### 자주 쓰이는 용법
- 메서드의 this와 메서드 내부의 중첩 or 콜백 함수의 this가 불일치할 때 사용
  - 헬퍼 함수 역할을 하는 함수는 외부 함수와 this가 일치하지 않으면 의도된 바와 다르게 실행될 수 있음
    ```javascript
    // person.foo()의 this가 변화하여 문제가 생기는 코드
    
    const person = {
      name: 'Lee',
      foo(callback) {
        setTimeout(callback, 100); // 호출 이전의 시점에서의 this는 person 객체가 됨
      }
    }
    
    person.foo(function() {
      // 호출된 시점의 this는 window를 가리킴
      console.log(`My name is ${this.name}`);
    });
    ```
    
    ```javascript
    // bind()를 통해 this를 일치시킨 코드
    const person = {
      name: 'Lee',
      foo(callback) {
        setTimeout(callback.bind(this), 100); // callback 함수에 foo 함수의 this인 person 객체를 전달
      }
    }
    
    person.foo(function() {
      // this가 person으로 유지됨
      console.log(`My name is ${this.name}`);
    });
    ```
- `setTimeOut()`을 클래스 메서드에 포함할 때 ([참조](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/bind#settimeout%EA%B3%BC_%ED%95%A8%EA%BB%98_%EC%82%AC%EC%9A%A9))
  - setTimeout의 this는 기본적으로 window 또는 global 객체이나, 특정 클래스 인스턴스 내의 메서드로 setTimeout을 사용할 경우 명시적으로 this를 바인딩할 수 있다.
    ```javascript
    function LateBloomer() {
      this.petalCount = Math.ceil(Math.random() * 12) + 1;
    }
    
    // 1초 지체 후 bloom 선언
    LateBloomer.prototype.bloom = function () {
      window.setTimeout(this.declare.bind(this), 1000);
    };
    
    LateBloomer.prototype.declare = function () {
      console.log("I am a beautiful flower with " + this.petalCount + " petals!");
    };
    
    var flower = new LateBloomer();
    flower.bloom();
    // 1초 뒤, 'declare' 메소드 유발
    ```

#### 레퍼런스
- <모던 자바스크립트 Deep Dive>
- [MDN Function.prototype.apply()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
- [MDN Function.prototype.call()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/call)
- [MDN Function.prototype.bind()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
