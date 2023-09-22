# 프로그래머스 정수 부분 풀이
> 푼 날짜: 23. 09. 22
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/181850)  
![image](https://github.com/makepin2r/TIL/assets/39889583/c567b157-9558-40ea-985c-5c20badea825)

## 나의 풀이
### 아이디어
정수부만 남기면 되기 때문에 `Math.floor`을 활용하여 실수부를 버림한다.
### 코드
```javascript
function solution(flo) {
    return Math.floor(flo);
}
```
위의 코드로 통과하긴 했으나, 엄밀히 따져서 문제의 의도에 맞게 하려면 floor가 아닌 다른 방식을 써야 한다는 생각이 들었다.  
문제의 경우 매개변수의 범위가 0~100 사이이기 때문에 상관 없었겠지만,  
만약 음의 정수까지 포함된 경우 floor을 사용하면 안됐을 것이다.  
음의 정수는 버림을 했을 때 정수부가 그대로 유지되지 않기 때문이다.  
예를 들어 Math.floor(-17.8)은 -18이다.  

## 알게 된 것
### Math.trunc
문제의 의도에 좀더 정확히 들어맞는 메서드가 있어 학습하였다.  
`Math.floor`의 경우 매개변수로 주어진 수보다 작은 정수 중 가장 큰 수를 반환한다.  
> Math.floor() 함수는 주어진 숫자와 같거나 작은 정수 중에서 가장 큰 수를 반환합니다.
> (출처: MDN)

`Math.trunc`는 매개변수의 실수부를 제거하고 정수부만 반환하는 메서드이다.

> Math.trunc() 함수는 주어진 값의 소수부분을 제거하고 숫자의 정수부분을 반환합니다.
> (출처: MDN)

그러므로 Math.floor(-17.8)은 -18이 되며, Math.trunc(-17.8)은 -17이 된다.

---
#### 레퍼런스
[MDN Math.floor](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
[MDN Math.trunc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc)
