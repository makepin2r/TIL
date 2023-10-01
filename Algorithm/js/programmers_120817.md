# 프로그래머스 배열의 평균값 풀이
> 푼 날짜: 2023. 10. 01
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120817)  
![image](https://github.com/makepin2r/TIL/assets/39889583/a188704d-d735-4d41-ba72-4feab7df7422)

## 나의 풀이
```javascript
function solution(numbers) {
    return numbers.reduce((total, value) => total + value) / numbers.length;
}
```
`reduce`를 이용해 전체 배열 요소의 합을 구한 후, 배열의 길이로 나누어준다.

## 다른 사람 풀이
모든 풀이가 유사하여 생략.
