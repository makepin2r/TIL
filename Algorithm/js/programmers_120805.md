# 프로그래머스 몫 구하기 풀이
> 푼 날짜: 2023. 09. 27
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120805)  
![image](https://github.com/makepin2r/TIL/assets/39889583/19a06f6c-5d68-49bc-ab2c-236aa9074852)

## 나의 풀이
```javascript
function solution(num1, num2) {
    return parseInt(num1 / num2);
}
```

## 다른 사람 풀이
```javascript
function solution(num1, num2) {
    return Math.trunc(num1 / num2);
}
```
예전 [정수 부분](https://github.com/makepin2r/TIL/blob/main/Algorithm/js/programmers_181850.md)을 풀 때에 `trunc`를 알게 된 적이 있다.  
생각해보니 몫을 정확히 구하려면 반올림/버림 등이나 parseInt보다는 trunc를 쓰는 것이 맞다.

```javascript
function solution(num1, num2) {
    return (num1 / num2)<<0;
}
```
새로운 것을 배웠다.  
`<<`의 피연산자로 0을 사용하면 실제 이동이 발생하지 않으나,  
JS에서는 비트 연산시 피연산자를 32bit 정수로 변환하기 때문에 `trunc`와 같은 효과를 낸다. 즉 소수 부분이 잘려나간다.

```javascript
function solution(num1, num2) {
    return ~~(num1/num2);
}
```
~ 연산자를 두 번 사용하여 소수 부분을 버리는 방식의 풀이.  
이렇게 했을 때도 `trunc`와 같은 효과를 낼 수 있다.

## 알게 된 것
### <<의 피연산자 처리
> 왼쪽 피연산자는 32비트 정수로 변환됩니다. 즉, 부동 소수점 숫자는 잘리고 32비트 경계 내에 있지 않은 숫자는 오버플로우/언더플로우됩니다.
> 오른쪽 피연산자는 부호 없는 32비트 정수로 변환된 다음 32 나머지 연산의 값을 가져오므로 실제 시프트 오프셋은 항상 0에서 31 사이의 양의 정수입니다. 예를 들어, 100 << 32는 100 << 0과 동일(이 결과값은 100입니다)합니다. 32 나머지 연산은 0이기 때문입니다.
`<<`(왼쪽 시프트 연산자) 사용시 피연산자들이 모두 32비트 정수로 변환된다.
### `~~` 연산자
`~`(틸트) 연산자는 피연산자를 이진수를 변환한 다음 해당 비트를 모두 NOT 연산한다.  
예를 들어 ~1 의 경우 00000001(2) 가 11111110(2)로 변환된다.  
모든 비트 연산의 경우 소수점 아래 값은 버리게 되므로,  
~~ 처럼 틸트 연산자를 연달아 두번 사용하면 원래의 값에서 소수 부분만 버려지는 효과가 생긴다.

---
#### 레퍼런스
- [MDN 왼쪽 시프트 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Left_shift)
- [MDN 비트 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Expressions_and_operators#%EB%B9%84%ED%8A%B8_%EC%97%B0%EC%82%B0%EC%9E%90)
- https://castellan.tistory.com/51
