# 표준 내장 객체의 확장
## 표준 내장 객체 Standard built-in object
- 자바스크립트가 기본적으로 제공하는 객체 (+ 호스트 환경에서 제공하는 추가 기능들)
    - 이 객체들을 바탕으로 개발자는 소프트웨어를 위한 추가 기능들을 만든다. == **사용자 정의 객체**
    - Object, Function, Array 등 ...
- 사용자 정의 객체가 아닌 기존 내장 객체를 확장해 사용하는 방법도 있다.

## 표준 내장 객체 확장 예시 - 배열
- `prototype`을 사용한다.

```javascript
// 표준내장객체인 Array의 생성자함수 prototype에 함수를 추가한다. -> 모든 배열에서 해당 기능을 사용할 수 있다.
Array.prototype.rand = function(){
    var index = Math.floor(this.length*Math.random());
    return this[index];
}

var arr = new Array('seoul','new york','ladarkh','pusan', 'Tsukuba');
console.log(arr.rand());
```