# 렉시컬 스코프 (Lexical Scope)

## 스코프 (Scope, 유효 범위)
> 현재 실행되는 컨텍스트를 말한다.
> 여기서 컨텍스트는 값과 표현식이 **"표현"**되거나 참조 될 수 있음을 의미한다.
> 만약 변수 또는 다른 표현식이 "해당 스코프"내에 있지 않다면 사용할 수 없다.
> 스코프는 또한 계층적인 구조를 가지기 때문에 하위 스코프는 상위 스코프에 접근할 수 있지만 반대는 불가하다.
> (출처 : MDN)
- **참조 대상** 식별자를 찾아내기 위한(식별자가 유효한 범위) 규칙
  - 식별자: 변수명, 함수명 등 특정 대상을 다른 대상들과 구분하여 식별할 수 있는 고유한 이름
- 프로그래밍 언어는 크게 두 가지 스코프 중 하나의 방식을 따름
  - 동적 스코프
  - 렉시컬 스코프 (정적 스코프)

## 렉시컬 스코프 (Lexical Scope, 정적 스코프)
- **함수 선언의 위치**를  기준으로 스코프가 정해진다. 
  - 코드가 쓰여진 순간에 스코프 체인이 정해지고 함수 실행 순서와 관계 없음
- JS를 포함한 대부분의 프로그래밍 언어가 따르는 스코프 방식
```javascript
var x = 1;

function foo() {
	var x = 10;
	bar();
}

function bar() {
	console.log(x);
}

foo(); // 1
bar(); // 1
```
- 위의 `bar` 함수의 상위 스코프는 전역 스코프
  - 선언부가 전역에 있기 때문
  - `foo` 함수 내에서 호출되더라도 `bar` 내의 x 변수는 전역 변수를 참조

### 동적 스코프 
- 함수 호출을 기준(함수 실행 순서)로 스코프가 정해짐
  - 즉 상위 스코프가 가장 최근 실행된 함수의 스코프가 됨
  - 호출이 어디에서 되었는가가 중요하며, 코드 내의 중첩이 아닌 콜스택과 관련이 있음
```javascript
// JS가 동적 스코프를 사용한다면?
function test() {
    console.log(a);
}

function main() {
    var a = 3;
    test();
}

var a = 2;
main(); // 렉시컬 스코프일 경우 2, 동적 스코프일 경우 3
```
- JS의 경우 렉시컬 스코프를 따르므로, 전역에서 작성된 test 내의 a는 전역 변수 a인 2를 가리킨다.
- 동적 스코프를 따를 경우 콜스택에 전역 → main → test가 쌓이므로, test의 상위 스코프는 main이 된다.
  즉 test 내의 a는 main의 a를 가리키므로 3이 된다.

---
#### 레퍼런스
- [MDN 스코프](https://developer.mozilla.org/ko/docs/Glossary/Scope)
- https://dean30.tistory.com/100
- https://velog.io/@chojs28/%EB%A0%89%EC%8B%9C%EC%BB%AC-%EC%8A%A4%EC%BD%94%ED%94%84%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%80-%EA%B7%B8%EB%A6%AC%EA%B3%A0-%EC%BB%A4%EB%A7%81
- https://chati.tistory.com/158
