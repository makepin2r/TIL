# 프로그래머스 최댓값 만들기(1) 풀이
> 푼 날짜: 2023. 10. 03
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120847)  
![image](https://github.com/makepin2r/TIL/assets/39889583/85f4e144-1bc0-431b-b239-90db8a43ce67)
## 나의 풀이
```javascript
function solution(numbers) {
    numbers.sort((a, b) => b - a);
    return numbers[0] * numbers[1];
}
```
`sort`를 이용해 원소들을 내림차순으로 정렬 후,  
0번째 요소와 1번째 요소를 곱해 반환한다.
## 다른 사람 풀이
```javascript
function solution(numbers) {
    let [a, b] = numbers.sort((a,b) => b - a);
    return a * b;
}
```
비구조화 할당을 써서 깔끔하게 작성한 풀이.
