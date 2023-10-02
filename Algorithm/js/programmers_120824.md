# 프로그래머스 짝수 홀수 개수 풀이
> 푼 날짜 : 2023. 10. 02
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120824)  
![image](https://github.com/makepin2r/TIL/assets/39889583/b73f9d83-4ba1-4bde-b343-25e0346e6e6d)
## 나의 풀이
```javascript
function solution(num_list) {
    const even = num_list.reduce((total, v) => total += v % 2 === 0 ? 1 : 0, 0);
    return [even, num_list.length - even];
}
```
- `reduce` 메서드를 통해 짝수 원소의 개수만 카운트한다.
- num_list의 길이 - 짝수 원소의 갯수가 홀수가 되므로, 카운트한 짝수 원소 갯수와 배열 길이 - 짝수 갯수를 배열에 담아 반환한다.

## 다른 사람 풀이
```javascript
function solution(num_list) {
    var answer = [0,0];

    for(let a of num_list){
        answer[a%2] += 1
    }

    return answer;
}
```
for of 문을 활용한 센스있는 풀이!  
짝수일 경우 2에 대한 나머지 연산이 0, 홀수일 경우 1이 되는 것을 인덱스로 활용해 반복문을 돌며 1씩 더해준다.
```javascript
function solution(list) {
    return list.reduce((acc, cur) => (cur & 1 ? acc[1]++ : acc[0]++, acc), [0, 0])
}
```
비트 연산을 활용한 풀이이다.  

## 알게 된 것
### 비트 AND 연산을 이용한 홀짝 구분
`숫자 & 1` 비트 연산을 할 경우 홀짝을 빠르게 구분할 수 있다.  
숫자 1은 2진수로 '001'이기 때문에, 홀수와 & 연산을 진행할 경우 항상 1을 반환하고 짝수일 경우 0을 리턴하기 때문이다.  

---
### 레퍼런스
- [MDN AND 비트연산(&)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Bitwise_AND)
