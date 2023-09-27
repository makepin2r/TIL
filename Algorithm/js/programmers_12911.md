# 프로그래머스 다음 큰 숫자 풀이
> 푼 날짜: 2023. 09. 27
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/12911)  
![image](https://github.com/makepin2r/TIL/assets/39889583/bd43f802-9d48-4868-a0fb-f32cca2522c6)

## 나의 풀이
### 아이디어
1. n의 1 개수를 구한다.
    - `toString([진법수])` 메서드를 활용해 2진수로 변환한다.
    - 변환한 2진수 문자열에 `split(1)` 를 적용하면 1의 갯수 + 1만큼 배열이 반환되므로, 결과값 - 1이 2진수로 변환했을 때의 1의 갯수가 될 것이다.
2. 반복문을 돌며 n+1 부터 1의 방식으로 2진수 내 1의 갯수를 구해 비교 후, 조건 만족시 반환한다.
### 코드
```javascript
function solution(n) {
    const oneCount = n.toString(2).split('1').length - 1;
    let num = n + 1;
    while(true){
        if(num.toString(2).split('1').length - 1 === oneCount) return num;
        ++num;
    }
}
```

## 다른 사람 풀이
```javascript
function solution(n,a=n+1) {
    return n.toString(2).match(/1/g).length == a.toString(2).match(/1/g).length ? a : solution(n,a+1);
}
```
정규식과 재귀 함수 방식을 사용한 풀이이다.   
2진수로 변환된 n에 `match` 메서드로 정규식을 적용해 갯수를 구한 다음 조건에 맞지 않으면 계속 더 큰 숫자와 비교한다.

```javascript
function nextBigNumber(n) {
    var i, j;
    for (i = 0; !(n & 1); i++) {n = n >> 1; } // 1을 찾을때까지 우로 쉬프트, 쉬프트 횟수 = i
    for (j = 0; n & 1; i++, j++) {n = n >> 1; } // 0을 찾을때까지 우로 쉬프트, 1의 갯수 = j
    for (j--, n++; i !== j; i--) {n = n << 1; } // 0자리에 1대입, 1의 갯수 -1, i === j 가 될때까지 죄로 쉬프트하면서 쉬프트 횟수 -1
    for (i; i; i--, n++) {n = n << 1; } // i === 0 될때까지 좌로 쉬프트 하면서 쉬프트 횟수 -1, 0자리에 1대입
    return n;
}
```
쉬프트 연산자를 사용한... 엄청난 풀이  

---
#### 레퍼런스
- https://gent.tistory.com/467
- https://medium.com/web-dev-note/javascript-%EC%A7%84%EB%B2%95-%EB%B3%80%ED%99%98-330694083495
