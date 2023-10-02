# 프로그래머스 점의 위치 구하기 풀이
> 푼 날짜: 2023. 10. 02
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120841)  
![image](https://github.com/makepin2r/TIL/assets/39889583/0a6d20a0-3e51-4c8d-918a-85d771e11beb)

## 나의 풀이
```javascript
function solution(dot) {
    return dot[0] > 0 ? (dot[1] > 0 ? 1 : 4) : (dot[1] < 0 ? 3 : 2);
}
```
문제의 조건에 따라 중첩된 삼항 연산자로 풀었다.

## 다른 사람 풀이
```javascript
function solution(dot) {
    const [num,num2] = dot;
    const check = num * num2 > 0;
    return num > 0 ? (check ? 1 : 4) : (check ? 3 : 2);
}
```
나의 풀이와 비슷하게 삼항 연산자로 풀었지만,  
check 변수로 두 수가 서로 부호가 같은지 체크하는 것으로 가독성이 훨씬 좋아진 풀이이다.
