# 함수의 arguments

## arguments란?
- 함수의 전달된 인자를 담고 있는 **객체**
  - 함수 안에서 약속되어진 객체로, arguments라는 객체의 인스턴스 
  - 사용 방법이 배열과 유사하다.

- `arguments.length` : 전달된 인자의 개수
- `arguments[i]` : i번째 순서에 있는 인자

```javascript
function sum(){ // 매개변수가 없는 함수
    var i, _sum = 0;    
    for(i = 0; i < arguments.length; i++){
        document.write(i+' : '+arguments[i]+'<br />');
        _sum += arguments[i];
    }   
    return _sum;ㄴ
}
document.write('result : ' + sum(1,2,3,4)); // javascript는 인자의 개수와 매개변수의 개수와 일치하지 않더라도 용인해준다.
```
---
## 함수.length & arguments.legnth
- [함수명].length : 함수에 정의된 매개변수의 수
- arguments.legnth : 함수를 호출할 때 실제로 전달된 인자의 수

- 두 값을 비교해 함수가 의도된 대로 사용되는지 체크하는 등에 활용할 수 있다.

```javascript
function zero(){ // 매개변수가 0개인 함수
    console.log(
        'zero.length', zero.length, // 정의된 매개변수의 개수
        'arguments', arguments.length // 실제 전달된 인자의 개수
    );
}

// 매개변수가 0개로 정의된 함수에, 1개의 인자를 전달하였으므로
zero(1); // zero.length 0 arguments 1
```

