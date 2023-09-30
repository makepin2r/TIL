# 프로그래머스 크기가 작은 부분 문자열 풀이
> 푼 날짜 : 2023. 09. 30
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/147355)  
![image](https://github.com/makepin2r/TIL/assets/39889583/d4b3ac1c-7305-4405-81e6-88d6c66b6a2f)
## 나의 풀이
### 아이디어
`substr`을 이용해 p의 문자열 길이만큼 잘라 p와 비교한다.
### 코드
```javascript
function solution(t, p) {
    let count = 0;
    for(let i = 0; i <= t.length - p.length; ++i){
        Number(t.substr(i, p.length)) <= Number(p) && ++count;
    }
    return count;
}
```
## 다른 사람 풀이
```javascript
function solution(t, p) {
    let count = 0;
    for(let i=0; i<=t.length-p.length; i++) {
        let value = t.slice(i, i+p.length);
        if(+p >= +value) count++;
    }
    return count;
}
```
나의 풀이와 로직은 같으나 문자열 → 숫자 변환에 `Number`가 아닌 `+` 연산자를 사용하였다.
