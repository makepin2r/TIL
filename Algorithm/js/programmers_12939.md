# 프로그래머스 최댓값과 최솟값 풀이
> 푼 날짜 : 23. 09. 18

## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/12939)
![image](https://github.com/makepin2r/TIL/assets/39889583/00762278-41eb-4049-8857-90b70727ce12)

## 나의 풀이
### 아이디어
1. `split()` 메서드를 이용하여 숫자들을 배열로 저장
2. 문자열로 저장되어있으므로, 반복문을 돌며 모든 숫자들을 Number로 변경
3. `Math.min()`, `Math.max()` 메서드를 활용하여 최솟값과 최댓값을 리턴
### 풀이
```javscript
function solution(s) {
    let arr = s.split(" ");
    arr = arr.map(item => Number(item));
    return Math.min(...arr) + " " + Math.max(...arr);
}
```

## 다른 사람 풀이
```javascript
function solution(s) {
    const arr = s.split(' ');
    return Math.min(...arr)+' '+Math.max(...arr);
}
```
...? JS의 Math.min(), Math.max()는 문자열이어도 대소비교가 되나보다... 
충격!  

```javscript
function solution(s) {
    let min = Math.min.apply(null,s.split(" ").map(Number));
    let max = Math.max.apply(null,s.split(" ").map(Number));
    var answer = min+" "+max;
    return answer;
}
```
이 풀이를 통해 `apply()` 메서드를 처음 알게 되었다.

## 알게 된 것
### Function.prototype.apply()
apply는 첫 인자로 함수가 호출될 때의 this를 받으며, 두 번째 인자로 함수가 호출될 때의 인자값으로 사용될 유사 배열 객체가 들어간다.  
[Function.prototype.apply() 학습 내용 정리](https://github.com/makepin2r/TIL/tree/master/javascript)

## 레퍼런스
[MDN Function.prototype.apply()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
