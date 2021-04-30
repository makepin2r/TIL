# 프로토타입 prototype

## prototype이란?
- 자바스크립트에서 상속의 수단, 객체의 원형
- 생성자 함수를 호출할 때, 리턴해줄 객체의 원형이 prototype에 저장되어있다. 
- prototype에 저장된 속성들은 생성자를 통해서 객체가 만들어질 때 그(새로 만들어진) 객체에 연결된다.


## prototype chain
- 상속된 객체들의 프로토타입은 부모에서 자식으로 쭉 타고 내려가며 연결되어있다. 이 프로토타입의 연결고리를 **prototype chain**이라고 한다.
```javascript
function Ultra(){}
Ultra.prototype.ultraProp = true;
 
function Super(){}
Super.prototype = new Ultra();
 
function Sub(){}
Sub.prototype = new Super();
 
var o = new Sub();
console.log(o.ultraProp); // true
```
- `o.ultraProp`에서 실행되는 일은 
    1. 객체 o에서 ultraProp를 찾는다.
    2. 없다면 Sub.prototype.ultraProp를 찾는다. (해당 객체의 생성자의 prototype)
    3. 없다면 Super.prototype.ultraProp를 찾는다. (해당 객체의 부모의 생성자의 prototype)
    4. 없다면 Ultra.prototype.ultraProp를 찾는다.
- (Sub 객체인) o가 `Ultra.prototype.ultraProp`에 접근할 수 있는 이유는 프로토타입 체인으로 연결되어있기 때문이다.


- 예시 코드 한 번 더
```javascript
// Ultra -> Super -> Sub 순서로 상속한 상태
var s = new Super();
s.ultraProp = 3;
Sub.prototype = s; // s 객체의 속성값이 prototype으로 지정됨

var o = new Sub();
console.log(o.ultraProp); // 3
```

### 주의할 점
- 생성자 함수가 아닌 상속할 함수의 prototype 객체를 바로 할당해버리면 문제가 발생한다.
  - 자식 객체의 prototype을 변경하면 부모 객체의 prototype에도 반영되기 때문이다.
```javascript
function Sub(){}

Sub.prototype = Super.prototype; // X
Sub.prototype = new Super(); // O
```