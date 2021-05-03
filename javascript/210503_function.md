# 함수 Function 
- 로직을 함수화해 재사용성, 유지보수, 가독성을 개선할 수 있다.
## 함수의 정의와 호출
- 함수의 정의 형식
```javascript
function 함수( [인자...[,인자]] ){
   코드
   return 반환값
}
```
```javascript
// 함수를 정의하는 또다른 방식
var 함수 = function(){
    코드
    return 반환값
}
```
- 함수 호출하기
```javascript
// 정의된 함수 myFunc
function myFunc() {}

// 함수 호출하기
myFunc();
```
## 함수의 입력과 출력
### 인자 argument
- 함수에 들어오는 입력값
    - 함수 호출부의 소괄호를 통해 전달할 수 있다.
    - 전달된 인자는 함수의 **매개변수**에 순서에 맞게 할당된다. 
```javascript
function myFunc(arg1, arg2) {} // arg1, arg2는 매개변수

myFunc(); // 인자로 1, 2 전달
```
### return
- 함수의 출력 담당
- 함수 내 `return` 키워드 뒤의 값은 함수의 결과로 반환되며, `return` 키워드가 있는 코드가 끝나면 함수가 종료된다.
```javascript
function myFunc1() {} 
function myFunc2() { return "Hello!"; } 

console.log(myFunc1()); // undefined
console.log(myFunc2()); // "Hello!"
```