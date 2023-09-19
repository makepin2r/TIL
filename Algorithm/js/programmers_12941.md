# 프로그래머스 최솟값 만들기 풀이
> 푼 날짜 : 23. 09. 19
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/12941)
![image](https://github.com/makepin2r/TIL/assets/39889583/ab926a26-99b1-437f-b074-1dc76c379bdf)

## 나의 풀이
### 아이디어
가장 큰 수와 가장 작은 수를 곱해주어야 최솟값이 나온다.  
그러므로 한 배열은 오름차순, 다른 배열은 내림차순으로 정렬한 뒤 곱하여 더해준다.

### 풀이
```javascript
function solution(A,B){
    A.sort((comp1, comp2) => comp1 - comp2);
    B.sort((comp1, comp2) => comp2 - comp1);
        
    return A.reduce((acc, cur, idx) => acc + cur * B[idx], 0);
}
```

## 다른 사람 풀이
내가 확인한 풀이들이 모두 나와 아이디어가 동일해 생략한다.
