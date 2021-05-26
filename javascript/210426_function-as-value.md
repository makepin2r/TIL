# 값으로서의 함수와 콜백

## 값으로서의 함수
- 자바스크립트에서는 함수도 객체, 즉 일종의 값.
- 함수가 값의 범위에 속하므로 가능해진 용도들이 있다.

### 1. 함수를 변수에 담기
- 값은 변수에 담을 수 있으므로 -> 함수 또한 값에 담을 수 있음.
```javascript
var a = 'value'; // 'value'라는 문자열은 값이므로 변수에 넣을 수 있다.
```
```javascript
function a () {} // a라는 변수에 함수를 담은 것
var a = function() {}; // 위의 코드와 동일
```

### 2. 함수를 객체의 속성에 담기 (method)
- 함수는 또한 객체 내의 값으로 포함될 수 있다.
    - 이러한 경우의 함수를 **메소드**라고 표현한다.
```javascript
a = {
    b : function(){
        // b: key, 변수, 속성(property)
        // b 안의 function : value, method
    }
}
```

### 3. 함수를 함수의 인자로 전달하기
- 함수를 인자로 전달할 수 있다.
    - 이로 인해 **콜백** 패턴이 가능해진다.

### 4. 함수를 함수의 리턴값으로 사용하기
```javascript
function cal(mode){
    var funcs = {
        'plus' : function(left, right){return left + right},
        'minus' : function(left, right){return left - right}
    }
    return funcs[mode]; // 리턴 형태가 함수
}

// 리턴된 함수에 인자를 다시 넣어 실행하는 구조
alert(cal('plus')(2,1));  // cal('plus')의 리턴은 function(left, right){return left + right} 이므로, 2 + 1 = 3이 출력된다.
alert(cal('minus')(2,1));   
```

### 5. 함수를 배열의 값으로 넣기
- 배열은 값의 컨테이너이므로 함수 또한 배열의 값으로 사용 가능하다.
```javascript
var process = [
    function(input){ return input + 10;},
    function(input){ return input * input;},
    function(input){ return input / 2;}
];
var input = 1;
for(var i = 0; i < process.length; i++){
    input = process[i](input);
}
alert(input);
```
---
## 일급 함수
### First-class citizen

- 변수, 매개변수, 리턴값으로 사용할 수 있는 데이터

> 컴퓨터 프로그래밍 언어 디자인에서, 일급 객체(영어: first-class object)란 다른 > 객체들에 일반적으로 적용 가능한 연산을 모두 지원하는 객체를 가리킨다. 보통 함수에 매개변수로 넘기기, 수정하기, 변수에 대입하기와 같은 연산을 지원할 때 일급 객체라고 한다.
> 
> 출처 : [위키피디아 - 일급 객체](https://ko.wikipedia.org/wiki/%EC%9D%BC%EA%B8%89_%EA%B0%9D%EC%B2%B4)

- 자바스크립트에서는 이 일급 객체의 범위 안에 함수도 들어간다. 

> 함수를 다른 변수와 동일하게 다루는 언어는 일급 함수를 가졌다고 표현합니다. 예를 들어, 일급 함수를 가진 언어에서는 함수를 다른 함수에 매개변수로 제공하거나, 함수가 함수를 반환할 수 있으며, 변수에도 할당할 수 있습니다.
>
> 출처 : [MDN - 일급 함수](https://developer.mozilla.org/ko/docs/Glossary/First-class_Function)
---
## 콜백
> 프로그래밍에서 콜백(callback) 또는 콜애프터 함수(call-after function)는 다른 코드의 인수로서 넘겨주는 실행 가능한 코드를 말한다. 콜백을 넘겨받는 코드는 이 콜백을 필요에 따라 즉시 실행할 수도 있고, 아니면 나중에 실행할 수도 있다.
>
> 출처: [위키백과 - 콜백](https://ko.wikipedia.org/wiki/%EC%BD%9C%EB%B0%B1)

### 처리 위임
- 인자로 함수를 전달해서, 기존 함수의 동작을 바꿀 수 있다. (= 사용자에게 동작의 방식 결정을 위임한다)
```javascript
var numbers = [20, 10, 9,8,7,6,5,4,3,2,1];
function sortNumber(a,b){
    return b-a;
}

alert(numbers.sort(sortNumber)); // array, [20,10,9,8,7,6,5,4,3,2,1]
```
- 위 예시의 `numbers.sort()`는 자바스크립트에서 기본으로 제공하는 **내장 메소드**이다. 이 함수에는 직접 정의한 함수를 인자로 전달해 정렬 로직을 변경할 수 있다. 

#### 내장 객체 & 내장 메소드, 사용자 정의 객체 & 사용자 정의 메소드
- **내장 객체**(빌트인 객체) :  자바스크립트에서 기본으로 제공하는 객체 ex. 배열 객체
- **내장 메소드**(빌트인 메소드) : 내장객체 내의 기본 메소드 ex. 배열 객체 내의 `sort()`

- 내장 객체, 내장 메소드 외 사용자가 직접 만드는 것들은 각각 **사용자 정의 객체**, **사용자 정의 메소드**라고 칭한다.

---
## 비동기 처리에서의 콜백
### 비동기적 처리란?
- 여러개의 연속된 로직이 있을 때, 앞의 로직이 끝날 때까지 뒤의 로직들이 기다리지 않고 먼저 실행되게끔 하는 방법
    - 서버와의 통신에서 진행되는 작업이 너무 길거나 소요 시간을 예상할 수 없는 경우, 화면의 다른 기능들이 정상적으로 작동하게 하려면 비동기 처리가 필요하다.
### Ajax 
- 비동기적인 서버통신 방법
  - 콜백함수를 통해 사용자에게 커스텀되는 동작을 위임한다.
```javascript
    $.get('./datasource.json.js', function(result){
        console.log(result);
    }, 'json'); // 두 번째 인자가 콜백 함수, 서버랑 통신이 끝났을 때 호출되도록 세팅됨
```
