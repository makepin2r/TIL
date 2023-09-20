# 프로그래머스 x 사이의 개수 풀이
> 푼 날짜: 23. 09. 20

## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/181867)
![image](https://github.com/makepin2r/TIL/assets/39889583/ff804b2c-81f1-4b94-bb92-9ff51209a96f)

## 나의 풀이
### 아이디어
`split` 메서드를 이용하면 특정 문자열을 기준으로 문자열을 나눌 수 있다.  
나뉜 결과값은 배열로 반환되므로, `map` 메서드를 활용해 각 요소의 length값을 반환한다.
### 풀이
```javascript
function solution(myString) {
    return myString.split("x").map(item => item.length);
}
```

## 다른 사람 풀이
```javascript
const solution = (myString) => {
    const arr = myString.split('x');
    // console.log(arr)
    return arr.reduce((a,c)=>[...a,c.length],[]);
}
```
같은 로직이나 `reduce`를 활용한 풀이.
