#  객체로서의 자바스크립트 함수
- 자바스크립트에서 함수는 객체다.  
    - `Function`이라는 객체의 인스턴스이다.
```javascript
    // Function 생성자를 이용해 함수를 정의
    var sum1 = new Function('x', 'y', 'return x+y;');
    sum1(1, 2); // 3

    // 하지만 위의 코드는 사용이 불편하기 때문에 
    // 보통 함수 리터럴을 활용해 정의하는 경우가 많다.
    function sum2(x, y) {
        return x + y;
    }
    sum2(1, 2); // 3
```