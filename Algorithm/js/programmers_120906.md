# 프로그래머스 자릿수 더하기 풀이
> 푼 날짜: 2023. 10. 02
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120906)  
![image](https://github.com/makepin2r/TIL/assets/39889583/f6dbc610-3494-46c1-b496-ee81bbb66b70)
## 나의 풀이
```javascript
function solution(n) {
    return [...n.toString()].reduce((total, v) => total += +v, 0);
}
```
매개변수 n을 문자열로 변환해 배열로 만든 다음, 다시 숫자로 각 자릿수를 변환하여 더해주었다.  
형변환이 두 번이나 일어나며 스프레드 연산자나 reduce까지 썼기 때문에 효율적인 코드는 아닐 수 있겠다는 생각이 들었다.  
10의 n제곱과의 나머지 연산을 통해 자릿수를 구할 수는 있겠으나, 반복문이 돌아야 하는 기준을 떠올리지 못해 코드로 구현하지 못했다.

## 다른 사람 풀이
```javascript
function solution(n) {
    let result = 0;
    while (n > 0) {
        result += n % 10;
        n = Math.floor(n/10);
    }
    return result;
}
```
형변환 없이 숫자만으로 구현한 방식이다.  
생각해보니 굳이 숫자의 자릿수 크기나 10의 몇제곱부터 나눠야 하는지 고려하지 않아도 되었다.  
## 알게 된 것
### 형변환 없이 자릿수 구하기
```javascript
// 숫자 num이 있을 때
while (n > 0) {
  n % 10; // 숫자의 1의 자리만 구할 수 있음
  Math.floor(n/10); // 10으로 나누면 1의 자리만 소수점이 되므로, 소수부를 Math.floor로 제거하면 자릿수가 숫자별로 10단위씩 낮아진다.
}
```
