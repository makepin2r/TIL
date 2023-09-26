# 프로그래머스 a와 b 출력하기 풀이
> 푼 날짜: 2023. 09. 24
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/181951)
![image](https://github.com/makepin2r/TIL/assets/39889583/b440aed3-4667-472e-9c26-8fc62877294d)

## 풀이
```javascript
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

let input = [];

rl.on('line', function (line) {
    input = line.split(' ');
}).on('close', function () {
    console.log(`a = ${input[0]}`);
    console.log(`b = ${input[1]}`);
});
```
