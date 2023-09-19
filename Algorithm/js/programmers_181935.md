# 프로그래머스 홀짝에 따라 다른 값 반환하기 풀이
> 푼 날짜 : 23. 09. 19

## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/181935)
![image](https://github.com/makepin2r/TIL/assets/39889583/de009cc9-d80c-4e04-900a-41543dd38e70)

## 내 풀이
```javascript
function solution(n) {
    let answer = 0;
    while(n > 0) {
        answer += (n % 2 === 0 ? n**2 : n);
        n -= 2;
    }
    return answer;
}
```
홀수든 짝수든 계산해야 할 수가 2씩 차이나며, 로직이 다른 부분은 합 or 제곱 여부이다.  
따라서 삼항 연산자를 사용해 홀수일 경우/짝수일 경우를 나누어 각각 합계를 다르게 한 뒤 결과를 반환한다.

## 다른 사람 풀이
```javascript
function solution(n) {
    if(n%2===1)
      return  (n+1)/2*((n + 1)/2) ;
    else
      return   n*(n+1)*(n+2)/6;
}
```
조건문 및 반복문을 사용하지 않는... 너무 멋진 풀이...  
홀수일 경우 등차수열의 합 공식, 짝수일 경우 자연수의 거듭제곱 합 공식을 사용했다.
