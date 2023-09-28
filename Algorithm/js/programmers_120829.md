# 프로그래머스 각도기 풀이
> 푼 날짜: 2023. 09. 28
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120829)
![image](https://github.com/makepin2r/TIL/assets/39889583/ebef38b9-dd40-4a90-a34e-20e3ae039204)

## 나의 풀이
```javascript
function solution(angle) {
    return angle < 90 ? 1 : angle === 90 ? 2 : angle < 180 ? 3 : 4;
}
```
가독성은 떨어지지만... 짧은 코드로 써보고 싶었다.

## 다른 사람 풀이
```javascript
function solution(angle) {
    return [0, 90, 91, 180].filter(x => angle>=x).length;
}
```
`filter` 함수를 사용한 멋진 풀이다!  
가독성 좋은데 코드도 간결해지는 기발한 아이디어라고 생각한다.
