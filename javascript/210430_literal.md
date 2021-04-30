# 리터럴의 의미

### 1. 고정된 값

- 변수 또는 상수에 저장되는 데이터 그 자체
- 변수/상수는 메모리에 할당된 공간이라면
- 리터럴은 이 공간에 저장되는 값
    - 리터럴은 상수와 마찬가지로 메모리 어딘가에 값이 변하지 않도록 저장되지만 이름이 없다.

### 2. 코드상에서 데이터를 표현하는 방식 (리터럴 표기법)

- 변수를 선언함과 동시에 값을 지정해주는 표기법
    - {} 은 객체 리터럴 : new Object()
    - function sdfsdf() {}은 함수 리터럴 : new Function()
    - []은 배열 리터럴 : new Array()

    ```jsx
    // 이건 함수 리터럴(literal)
    function sum(x, y) {
    	return x + y;
    }
    sum(1, 2); // 3

    // Function 객체를 이용해 생성자로 함수를 정의할 수도 있다! 즉 함수는 객체
    var sum2 = new Function('x', 'y', 'return x+y;');
    sum2(1, 2); // 3
    ```

---

### 참고

[https://asfirstalways.tistory.com/21](https://asfirstalways.tistory.com/21)