# 프로그래머스 배열 뒤집기 풀이
> 푼 날짜: 2023. 10. 01
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120821)  
![image](https://github.com/makepin2r/TIL/assets/39889583/d5bf1b8e-7a00-4d94-a0ab-3f1e5f470368)
## 나의 풀이
```javascript
function solution(num_list) {
    const answer = [];
    num_list.map((v) => answer.unshift(v));
    return answer;
}
```
`unshift` 메서드를 사용해서 값을 뒤가 아닌 앞에서부터 집어넣어 역순을 만든다.
## 다른 사람 풀이
```javascript
function solution(num_list) {
    return num_list.reverse()
}
```
사실 JS 배열에는 `reverse` 메서드가 있다. 해당 메서드를 활용한 풀이.
```javascript
function solution(num_list) {
    return num_list.sort((a, b) => -1);
}
```
`sort` 메서드를 활용한 풀이이다.  
정렬의 결과값을 무조건 `-1`로 하면 두 요소의 순서가 바뀌게 된다.

## 알게 된 것
### sort 함수 관련 유의점
다른 풀이를 보며 sort 함수에 대해 조금 더 알아보다가 찾아낸 미처 몰랐던 사실들을 정리한다.
- sort 함수는 정렬의 복사본을 반환하지 않는다. 원 배열을 정렬하는 메서드이다.
    > 반환 값: 정렬한 배열. 원 배열이 정렬되는 것에 유의하세요. 복사본이 만들어지는 것이 아닙니다. (출처: MDN)
- sort 함수에 정렬 함수를 인자로 제공할 경우, 정렬 함수에 들어가는 인자 2개는 반드시 동일한 값을 반환해야 한다.
    > compareFunction(a, b)은 요소 a와 b의 특정 쌍이 두 개의 인수로 주어질 때 항상 동일한 값을 반환해야합니다. 일치하지 않는 결과가 반환되면 정렬 순서는 정의되지 않습니다. (출처: MDN)

---
#### 레퍼런스
- [MDN Array.prototype.sort()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
