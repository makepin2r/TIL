# 프로그래머스 문자열 돌리기 풀이
> 푼 날짜: 2023. 09. 24
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/181945)
![image](https://github.com/makepin2r/TIL/assets/39889583/71501128-5ddb-428e-9cf8-46b2a0dd5e15)

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
    str = input[0];
    str.split("").map(v => console.log(v))
});
```
