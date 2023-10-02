# 프로그래머스 아이스 아메리카노 풀이
> 푼 날짜: 2023. 10. 02
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120819)
![image](https://github.com/makepin2r/TIL/assets/39889583/ac19fe54-1ab6-4c8a-a15b-d4912dd95fda)
## 나의 풀이
```javascript
function solution(money) {
    return [Math.trunc(money / 5500), money % 5500];
}
```
`Math.trunc`를 통해 가진 돈 중 5500으로 나눈 몫을 구한다. (커피 잔 수)  
돈을 5500으로 나눈 나머지는 남은 돈이 된다.

## 다른 사람 풀이
풀이들이 모두 유사하여 생략.
