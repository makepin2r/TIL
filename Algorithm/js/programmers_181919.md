# 프로그래머스 콜라츠 수열 만들기

## 문제
https://school.programmers.co.kr/learn/courses/30/lessons/181919
![image](https://github.com/makepin2r/TIL/assets/39889583/fa5118e3-8a0c-40db-8378-99fd1f5198ba)

## 나의 풀이
```javascript
function solution(n) {
    const answer = [n];
    while(n > 1){
        n = n % 2 === 0 ? n / 2 : 3 * n + 1;
        answer.push(n);
    }
    return answer;
}
```
주어진 수를 원소로 갖는 배열을 초기화한 다음, 반복문을 돌며 규칙에 따라 값을 추가하는 간단한 방식이다.

## 다른 사람 풀이
```javascript
function solution(n, arr = []) {
    arr.push(n)
    if (n === 1) return arr
    if (n % 2 === 0) return solution(n / 2, arr)
    return solution(3 * n + 1, arr)
}
```
재귀 함수 형태의 풀이.
배열에 추가할 숫자와 숫자를 넣을 배열을 인자로 받는다.
제일 먼저 주어진 n을 배열에 넣고, 그 후 짝수인 경우 배열에 2로 나눈 수를 넣고 홀수인 경우 `3 * n + 1`을 넣는다.
