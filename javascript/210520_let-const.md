# let, const
es6에서 새롭게 생긴 변수 선언 방식.
## es5의 기존 변수 선언 방식
- 함수 단위 스코프만 지원
- 변수 재선언 허용, 호이스팅 → 잠재적 문제점을 인식하기 어려움
## let, const의 공통점
1. var(함수 단위 스코프 지원)과 달리 **블록 단위`{}` 스코프**를 지원한다.
2. 재선언이 불가능하다.
```javascript
// 재선언이 가능한 var
var a = 1;
var a = 3; // OK

// 재선언이 불가능한 let
let A = 2;
let A = 20; // error
```
### const
- 읽기 전용 변수 (상수와 같음)
- 재할당이 불가능하므로 선언시 초기화를 반드시 해주어야 함.

### let
- 재할당이 가능
- 선언 후 나중에 초기화가 가능하나, 반드시 값 할당 전에 변수가 선언되어있어야 한다. (Temporal Dead Zone)
    - 호이스팅이 일어나지 않는 것과는 다르다. let과 const도 호이스팅이 발생하지만, 값이 초기화되기 전에 변수에 접근하면 `ReferenceError`를 뱉을 뿐이다.
```javascript
myLet = 'hi!'; // ReferenceError
let myLet; 
```
---
#### 참고
- [What is the Temporal Dead Zone?](https://github.com/ajzawawi/js-interview-prep/blob/master/answers/es6/temporal-dead-zone.md)
