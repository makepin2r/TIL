# 프로그래머스 피보나치 수 풀이
> 푼 날짜: 2023. 10. 01
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/12945)  
![image](https://github.com/makepin2r/TIL/assets/39889583/2919a25a-77b5-4794-aa27-732fb173aae1)

## 나의 풀이
### 첫 번째 시도 (실패)
```javascript
function solution(n) {
    const fib = [0, 1];
    
    for(let i = 2; i <= n; ++i) {
        fib.push(fib[i - 1] + fib[i - 2]);
    }
    
    return fib[n] % 1234567;
}
```
간단히 반복문을 이용해 피보나치를 구현했다.  
그러나 왜인지 자꾸 실패가 떴고...  
처음에는 피보나치 수가 너무 커져서 에러가 나는 줄 알았다.   
### 두 번째 시도 (성공)
```javascript
function solution(n) {
    const fib = [0, 1];
    
    for(let i = 2; i <= n; ++i) {
        fib.push((fib[i - 1] + fib[i - 2]) % 1234567);
    }
    
    return fib[n];
}
```
무언가 이상한 예감이 들어 결국 검색해보았다.  
알고 보니 문제에서 의미하는 바는 n번째 피보나치 수를 구한 뒤 그 수를 1234567로 나누어 리턴하라는 뜻이 아니라,  
매번 1234567로 나눈 나머지 수에 대한 피보나치를 구하라는 뜻이었다.
