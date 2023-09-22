# 프로그래머스 JadenCase 문자열 만들기
> 푼 날짜

## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/12951)
![image](https://github.com/makepin2r/TIL/assets/39889583/e5374656-8f21-482b-923d-dad80227b834)

## 나의 풀이
### 아이디어
1. 공백 단위로 `split` 메서드를 활용해 문자열을 자른다.  
2. 1에서 반환된 배열을 순회하며 잘린 문자열의 첫 번째 문자는 대문자로 변환, 나머지는 소문자로 변환해 붙여준다.
3. map 함수의 결과 배열을 `join` 메서드를 활용해 공백을 포함해 합친다.

### 코드 (실패)
```javascript
function solution(s) {
    return s.split(" ").map(v => v[0].toUpperCase() + v.slice(1, v.length).toLowerCase()).join(" ");
}
```
실행 결과 특정 테스트들에서 런타임 에러가 발생했다.

### 원인 및 수정한 코드 (성공)
문제는 연속 공백이었던 부분에서 발생함을 알 수 있었다.  
위 아이디어의 1번에서 연속 공백의 경우 빈 문자열`''`로 잘린다.
빈 문자열을 대괄호로 인덱스 접근했을 경우 `undefined`가 되는데,  
undefined에 `toUpperCase` 메서드를 실행했기 때문에 런타임 에러가 발생했다.
```javascript
function solution(s) {
    return s.split(" ").map(v => v.charAt(0).toUpperCase() + v.slice(1, v.length).toLowerCase()).join(" ");
}
```
인덱스로 접근하던 코드를 `charAt`으로 변경할 경우, 빈 문자열도 그대로 빈 문자열이 반환된다.

## 다른 사람 풀이
```javascript
function solution(s) {
    return s.split(" ").map(v => v.charAt(0).toUpperCase() + v.substring(1).toLowerCase()).join(" ");
}
```
같은 로직이나 문자열을 자르는 메서드인 `substring`을 활용했다.  
생각해보니 slice는 배열 메서드이니 substring을 활용하는 것이 더 맞았을 것 같고,  
substring은 끝 인덱스를 생략할 수 있어 가독성에도 더 도움이 될 것 같다.


---
#### 레퍼런스
- [MDN String.prototype.charAt()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)
