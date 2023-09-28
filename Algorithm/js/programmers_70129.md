# 프로그래머스 이진 변환 반복하기 풀이
> 푼 날짜: 2023. 09. 28
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/70129)  
![image](https://github.com/makepin2r/TIL/assets/39889583/7dd3b666-43c4-4669-a8ba-1bc109b3f1de)
## 나의 풀이
### 아이디어
1. s가 '1'이 될 때까지 반복문을 순회하며 아래 로직을 실행한다.
    1. 정규식을 이용해 s에 있는 모든 0을 제거한다.
    2. s의 문자열 길이 - 1의 결과 문자열 길이만큼 제거된 0 갯수 카운트를 더한다.
    3. 1의 결과 문자열 길이를 2진수로 변환하여 s에 대입한다.
    4. 변환이 이루어졌으므로 변환 횟수 카운트를 1 더한다.
2. 변환 횟수와 제거된 0의 갯수를 배열에 담아 반환한다.
### 코드
```javascript
function solution(s) {
    let [convertCnt, zeroCnt] = [0, 0];
    while(s !== '1'){
        const replaced = s.toString().replace(/0/g, "");
        zeroCnt += s.length - replaced.length;
        s = replaced.length.toString(2);
        ++convertCnt;
    }
    return [convertCnt, zeroCnt];
}
```

## 다른 사람 풀이
```javascript
function solution(s) {
    var answer = [0,0];
    while(s.length > 1) {
        answer[0]++;
        answer[1] += (s.match(/0/g)||[]).length;
        s = s.replace(/0/g, '').length.toString(2);
    }
    return answer;
}
```
`match`를 활용한 풀이이다.  
다만 이 경우에는 0이 포함되지 않은 경우 `null`이 반환되므로, `||[]`로 예외처리를 반드시 해주어야 한다.
