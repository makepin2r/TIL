# 전역객체 (Global object) (학습중)
## 전역객체
- 모든 객체(전역변수, 함수)는 **전역객체**의 프로퍼티다.
  - 객체를 명시하지 않으면 암시적으로 window의 프로퍼티로 간주됨

```javascript
var func = function(){}

// 두 코드는 동일
func();
window.func();
```

```javascript
var obj = {
    'func' : function(){}
}

// 두 코드는 동일
obj.func();
window.obj.func();
```

## 전역객체 API
- ECMAScript에서 정의한 전역객체(**Global**)의 API 
  - 전역 함수, 전역 변수를 정의하게 되면 Global 객체의 프로퍼티로써 정의되는 것.
  - 호스트 환경에 따라 전역객체의 이름은 달라질 수 있으나(ex. 웹브라우저 자바스크립트 : window), 모든 전역객체들은 이 API를 공통으로 가지고 있다.