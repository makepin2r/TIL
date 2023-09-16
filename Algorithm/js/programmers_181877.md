# 프로그래머스 대문자로 바꾸기 풀이
> 푼 날짜 : 23. 09. 14

## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/181877)
![181877](https://github.com/makepin2r/TIL/assets/39889583/7e255ff8-b28d-4cad-a85c-ed0020bfb9b3)

## 나의 풀이
```javascript
function solution(myString) {
    const small = "abcdefghijklmnopqrstuvwxyz";
    const capital = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    let result = myString;
    for(let i = 0; i < 26; ++i) {
        myString = result;
        const regex = new RegExp(`[${small[i]}]`, 'gi');
        result = myString.replace(regex, capital[i]);
    }
    return myString;
}
```
마음에 들지 않았던 풀이…  
단순히 `toUpperCase()`를 사용하지 않고 풀고 싶어 정규식을 활용한 방법을 생각해보았다.  
하지만 조금 지저분한 코드였다고 생각한다.  
기왕 정규식을 활용하니 모든 소문자를 한번에 대체할 수 있는 방법이 있을 거라고 생각했는데 실제로 구현해내지는 못한 점이 아쉽다.

## 다른 사람 풀이
```javascript
function solution(myString) {
  return myString.replace(/[a-z]/g, (match) => match.toUpperCase())
}
```
내가 실제로 구현하고 싶었던 방식으로 짜여진 답안이 있었다.  
replace의 두 번째 인자로 함수가 올 수 있다는 사실을 몰랐는데, 두 번째 함수로 감지된 대체될 소문자를 받아 대문자로 바꿔주면 된다.  
toUpperCase를 사용하긴 했으나 아주 좋은 방식이라고 생각한다.

## 알게 된 것
### `replace`의 두 번째 인자로 함수가 올 때
replace 함수의 두 번째 인자로 고정된 문자열이 아닌 함수가 올 수도 있다.  
만약 두 번째 인자에 함수가 들어올 경우,
> You can specify a function as the second parameter. In this case, the function will be invoked after the match has been performed. The function's result (return value) will be used as the replacement string. (출처 : MDN)
>
> 두 번째 인자로 함수를 명시할 수 있다. 이 경우, 함수는 (문자열이) 일치할 때마다 수행된다. 함수의 결과값은 대체될 텍스트로 사용된다.
이때 함수의 첫 번째 인자값은 replace에 의해 감지된 대체될 문자열이다.

## 레퍼런스
- [MDN String.prototype.replace()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
- [http://www.codejs.co.kr/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%97%90%EC%84%9C-replace%EB%A5%BC-replaceall-%EC%B2%98%EB%9F%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/](http://www.codejs.co.kr/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%97%90%EC%84%9C-replace%EB%A5%BC-replaceall-%EC%B2%98%EB%9F%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/)
