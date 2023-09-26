# 프로그래머스 문자열 출력하기 풀이
> 푼 날짜: 2023. 09. 27
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/181952)
![image](https://github.com/makepin2r/TIL/assets/39889583/b147e7d1-ba8e-47aa-a283-5279a2cb8913)

## 나의 풀이
```javascript
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

let input = [];

rl.on('line', function (line) {
    input = [line];
}).on('close',function(){
    console.log(input[0])
});
```
