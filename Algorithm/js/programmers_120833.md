# 프로그래머스 배열 자르기 풀이
> 푼 날짜: 2023. 10. 01
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120833)  
![image](https://github.com/makepin2r/TIL/assets/39889583/23b8371a-2875-442c-84db-e4df25f6f279)

## 나의 풀이
```javascript
function solution(numbers, num1, num2) {
    return numbers.slice(num1, num2 + 1);
}
```
`slice` 메서드를 활용하였다. 

## 다른 사람 풀이
```javascript
function solution(numbers, num1, num2) {
    return numbers.splice(num1, num2-num1+1);
}
```
배열을 자르는 다른 메서드 중 하나인 `splice`를 활용한 풀이.  
splice는 두 번째 인자로 자를 부분 배열의 길이가 와야 하기 때문에 `num2-num1+1`로 넣어야 한다.
