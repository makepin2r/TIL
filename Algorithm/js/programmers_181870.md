# 프로그래머스 ad 제거하기 풀이
> 1차 시도 날짜: 23. 09. 15
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/181870)
![image](https://github.com/makepin2r/TIL/assets/39889583/76463e05-370f-4a52-aa69-92378b7cea1c)

## 나의 풀이
```javascript
function solution(strArr) {
    return strArr.filter(item => item.indexOf("ad") === -1);
}
```
자바스크립트에서 문자열 내 특정 문자열이 포함되어있는지 여부를 확인할 수 있는 함수로
- `indexOf()`
- `includes()`
를 사용 가능하다.
나는 indexOf를 사용하고 인덱스가 없을 경우(-1 반환) filter를 이용해 걸러내는 방식을 사용했다.

## 다른 사람 풀이
```javascript
const solution = strArr => strArr.filter(v => !v.includes('ad'))
```
비슷한 방식이나 includes를 사용한 풀이이다.


## 레퍼런스
[MDN String.prototype.indexOf()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)
