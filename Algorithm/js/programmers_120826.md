# 프로그래머스 특정 문자 제거하기 풀이
> 푼 날짜 : 2023. 10. 03
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/120826)
![image](https://github.com/makepin2r/TIL/assets/39889583/09ebc65f-7ef4-4efa-97dd-086326d352c8)

## 나의 풀이
```javascript
function solution(my_string, letter) {
    return my_string.split(letter).join('');
}
```
`split` 메서드는 매개변수를 기준으로 나뉜 문자열 배열을 반환하며, 이 때 매개변수로 들어간 문자열은 제외된다.  
그러므로 반환된 배열을 다시 빈 문자열로 `join`한다.

## 다른 사람 풀이
```javascript
function solution(my_string, letter) {
    return my_string.replaceAll(letter, "");
}
```
`replaceAll`이라는 함수가 있는지 몰랐다!
```javascript
function solution(my_string, letter) {
    let reg = new RegExp(letter, 'g');
    return my_string.replace(reg, '');
}
```
정규식을 이용한 풀이이다.  
`replace`를 쓰더라도 정규식을 이용하면 중복 문자열 대체가 가능하다.

## 알게 된 것
### String.prototype.replaceAll
JS에서 relaceAll을 제공하는 줄 몰랐다.  
replaceAll의 인자는 두 가지가 들어간다.  

- 첫 번째 인자: 대체될 문자열 또는 정규식
- 두 번째 인자: 대체할 문자열
  
예를 들어 'strawberryjam'을 'applejam'으로 바꾸려면 이렇게 작성할 수 있다.  
```javascript
'strawberryjam'.replaceAll('strawberry', 'apple');
```
---
#### 레퍼런스
- [MDN String.prototype.replaceAll()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replaceAll)
