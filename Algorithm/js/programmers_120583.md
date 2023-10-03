# 프로그래머스 중복된 숫자 개수 풀이
> 푼 날짜 : 2023. 10. 03
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120583)  
![image](https://github.com/makepin2r/TIL/assets/39889583/52a207eb-f6fc-4cd1-a1f4-f11d03fd7f94)
## 나의 풀이
```javascript
function solution(array, n) {
    return array.reduce((total, v) => total + (v === n ? 1 : 0), 0);
}
```
`reduce`를 활용하였다. 원소의 값이 n과 같을 때만 카운트를 더해준다.
## 다른 사람 풀이
```javascript
function solution(array, n) {
    return array.filter(v=>v===n).length;
}
```
`filter`를 이용한 풀이.  
filter로 n과 일치하는 원소들만 추린 배열의 길이를 반환한다.
