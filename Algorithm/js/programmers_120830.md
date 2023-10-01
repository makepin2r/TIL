# 프로그래머스 양꼬치 풀이
> 푼 날짜: 2023. 10. 01
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120830)
![image](https://github.com/makepin2r/TIL/assets/39889583/b6cfad26-1ad8-41c0-b9d4-2811061cf18e)

## 나의 풀이
```javascript
function solution(n, k) {
    return n * 12000 + (k - Math.trunc(n / 10)) * 2000;
}
```
- 두 값을 더한다.
    - 양꼬치 값 : n인분 * 12,000원
    - 음료수 값 : (k개 - 서비스로 받은 음료수 갯수 (== n인분을 10으로 묶었을 때의 몫)) * 2,000원
## 다른 사람 풀이
```javascript
function solution(n, k) {
    k-=~~(n/10);
    if (k < 0) k = 0;
    return n*12000+k*2000;
}
```
내 풀이와 로직은 같으나, 틸트 연산자를 사용한 풀이.
