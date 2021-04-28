# 함수의 호출

## 함수를 호출하는 방법
### 1. 기본적인 방법
```javascript
function func(){
}
func(); // 기본적인 방법
```

### 2. apply()
- javascript에서 생성되는 모든 객체는 내장객체 `Function`의 인스턴스이다.
  - apply()는 Function에 소속된 내장 메소드이다.
  - javascript에서는 함수 또한 객체이기 때문에, 모든 함수는 apply()를 상속받는다.
  
- 인자의 종류
  1. 첫 번째 인자는 함수가 실행될 맥락 (= **this**가 될 대상)
     - 독립적 객체인 함수 sum()을 `sum.apply(o1)` 라고 호출했을 경우, `o1.sum()`과 같은 형태로 호출되는 것과 같다. (메소드처럼)
  2. 두 번째 인자에 들어가는 배열은 호출할 함수에 전달할 인자들

```javascript
function sum(arg1, arg2){
    return arg1+arg2;
}
alert(sum.apply(null, [1,2]))  // null은 맥락을 따로 지정하지 않는 것. 
```

```javascript
o1 = {val1:1, val2:2, val3:3}
o2 = {v1:10, v2:50, v3:100, v4:25}
function sum(){
    var _sum = 0;
    for(name in this){
        _sum += this[name];
    }
    return _sum;
}
alert(sum.apply(o1)) // o1.sum(); , 결과는 6
alert(sum.apply(o2)) // o2.sum(); , 결과는 185
```


