# 프로그래머스 짝수의 합 풀이
> 푼 날짜: 2023. 09. 30
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120831)  
![image](https://github.com/makepin2r/TIL/assets/39889583/d1c4f944-3192-4ec4-8fbc-9c7c9b10f706)
## 나의 풀이
### 아이디어
- 이 짝수일 경우 n부터, 아닐 경우 홀수이므로 n에서 1을 빼준 값부터 반복문을 통해 더해준다.
    - 짝수만 더하므로 2씩 빼며 더한다.
### 코드
```javascript
function solution(n) {
    let answer = 0;
    for(let i = (n % 2 === 0 ? n : n - 1); i > 0; i -=2)  {
        answer += i;
    }
    return answer;
}
```

## 다른 사람 풀이
```javascript
function solution(n) {
    var half = Math.floor(n/2);
    return half*(half+1);
}
```
자연수들의 합 공식인 `n(n+1)`을 활용한 풀이이다. 덕분에 반복문을 쓰지 않았다.  
n의 절반까지의 합을 구했기 때문에 짝수들끼리의 합과 동일해졌다.
```javascript
function solution(n) {
    return Math.floor(n / 2) * (2 + n) / 2 | 0
}
```
짝수 합을 계산하는 방법을 활용한 다른 풀이이다.  
짝수의 합은 첫 번째와 마지막 짝수의 평균을 계산한 다음, 평균과 짝수의 갯수를 곱하여 구할 수 있다.  
1부터 n까지의 수에서 짝수의 갯수는 n/2가 된다. 단 n이 홀수일 경우를 고려해 `Math.floor`로 한번 더 계산해준다.  
짝수의 평균은 `(2 + n) / 2`로 구하는데, 첫 번째 2는 첫 번째 짝수를 의미한다.  
마지막 `| 0`은 비트 OR 연산자로 `>> 0`을 이용했을 때와 유사하다.  
소수점 이하 부분이 제거되므로 `Math.floor`과 유사한 효과를 갖는다.
