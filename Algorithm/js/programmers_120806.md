# 프로그래머스 두 수의 나눗셈 풀이
> 푼 날짜: 2023. 09. 30
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120806)  
![image](https://github.com/makepin2r/TIL/assets/39889583/a1fc6b96-1517-41bc-bc09-1f24347f7db9)

## 나의 풀이
```javascript
function solution(num1, num2) {
    return Math.trunc(num1 / num2 * 1000);
}
```
정확한 정수부 출력을 위해 `trunc` 메서드를 사용했다.

## 다른 사람 풀이
```javascript
function solution(num1, num2) {
    return ~~(num1/num2*1000);
}
```
```javascript
function solution(num1, num2) {
    return num1*1000/num2<<0;
}
```
[예전에 풀었던 문제](https://github.com/makepin2r/TIL/blob/main/Algorithm/js/programmers_120805.md)에서 알게 됐던 방식을 사용한 풀이이다.  
틸트 연산자를 두번 사용하거나(~~) 비트 연산자로 `<<0` 하게 되면 32bit 정수로 변환되면서 `floor`와 같은 효과를 내며,  
Math 메서드를 활용했을 때보다 더 수행 속도가 빠르다.
