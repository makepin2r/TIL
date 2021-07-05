# 동치 연산자 Eqaul Operator (==와 ===의 비교)

## 두 동치 연산자의 차이
### Equal Operator ==
Equal Operator의 경우 값만 같으면 true, 아니면 false를 반환한다. 즉 강제적인 형변환(type coercion)이 일어난다.

### Strict Equal Operator ===
Strict Equal Operator는 자료형을 함께 비교한다.

### Strict Equal Operator의 여러 예시
#### 원시 자료형의 경우
- NaN과 NaN은 서로 다른 것으로 간주된다 (이건 일반 동치 연산자에서도 그러하다)
- null과 undefined는 서로 다른 것으로 간주된다
- 숫자 0, "0", ""은 모두 다르다.
- 숫자 1 &  true, 0 & false 는 서로 다르다

```javascript
console.log(null == undefined); // true 
console.log(null === undefined); // false

console.log(true == 1); // true 
console.log(true === 1); // false

console.log(0 == "0"); // true 
console.log(0 === "0"); // false 
console.log(0 == ""); // true 
console.log(0 === ""); // false

console.log(NaN == NaN); // false 
console.log(NaN === NaN); // false
```

#### 객체 자료형의 경우
배열이나 객체와 같은 객체 자료형에서는 변수마다 메모리 주소를 참조하기 때문에, 데이터 타입과 내부의 값이 같더라도 서로 다르다고 간주된다. (즉 어떤 변수에 다른 객체 자료형의 값을 할당했을 경우 같은 것으로 간주된다.)

```javascript
var a = [1,2,3]; 
var b = [1,2,3]; 
var c = b; 
console.log(b === c); // true 
console.log(b == c); // true
```

### 참고

- [https://steemit.com/kr-dev/@cheonmr/js-operator](https://steemit.com/kr-dev/@cheonmr/js-operator)
- [https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a](https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a)