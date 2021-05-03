# 정규표현식 Regular expression
- 문자열에서 특정 문자를 찾는데 사용되는 언어
- 정규표현식은 컴파일, 실행 두 단계로 이루어져있음
## 1. 컴파일
- 정규표현식 객체를 생성해 찾아내고자 하는 패턴을 만든다.
    - 정규표현식 객체 생성자
    ```javascript
    var pattern = new RegExp('a'); // a 라는 문자를 찾아내는 패턴
    ```
    - 정규표현식 리터럴: `//`를 사용한다
    ```javascript
    var pattern = /a/; // a 라는 문자를 찾아내는 패턴
    ```
## 2. 정규표현식 메소드 실행
### RegExp.exec()
- 패턴에 맞는 첫번째 일치 결과의 정보들을 배열로 리턴한다.
- 일치하는 결과가 없을 경우 null 리턴한다.
```javascript
console.log(pattern.exec('abc')); // ["a"]
console.log(pattern.exec('bcd')); // null
```
### RegExp.test()
- 패턴에 맞는 결과가 있을 경우 true, 없으면 false 리턴
```javascript
console.log(pattern.test('abc')); // true
console.log(pattern.test('bcd')); // false
```
## 정규표현식을 사용할 수 있는 문자열의 메소드
### String.match()
- 실행 결과는 `RegExp.exec()`과 같다.
    - `g` 옵션을 줄 경우 모든 일치 결과를 배열로 리턴한다 (exec()은 되지 않음)
```javascript
console.log('abc'.match(pattern)); // ["a"]
console.log('bcd'.match(pattern)); // null
```

### String.replace()
- 패턴을 검색한 뒤 인자로 넣어준 값으로 변경한 후, 변경된 값을 리턴
```javascript
console.log('abc'.replace(pattern, 'A'));  // Abc
```

## 옵션
- i: 대소문자를 구분하지 않는다.
- g: 검색된 모든 결과를 리턴한다.
```javascript
var pattern_i = /a/i;
var pattern_g = /a/g;
console.log('Abc'.match(pattern_i)); // ["A"]
console.log('abcabcabc'.match(pattern_g)); // ["a", "a", "a"]
```

## 캡처
- 그룹을 지정해 가져와 사용할 수 있는 기능
    - 괄호로 묶어서 지정할 수 있음
    - `$`와 숫자(순서)를 이용해 변수처럼 사용 가능
```javascript
// 생활코딩의 예시 코드 
var pattern = /(\w+)\s(\w+)/;
var str = "coding everybody";
var result = str.replace(pattern, "$2, $1");
console.log(result); // everybody coding
```

## 치환
```javascript
// 생활코딩의 예시 코드 
// url을 a 태그로 치환
var urlPattern = /\b(?:https?):\/\/[a-z0-9-+&@#\/%?=~_|!:,.;]*/gim;
var content = '생활코딩 : http://opentutorials.org/course/1 입니다. 네이버 : http://naver.com 입니다. ';
// urlPattern으로 탐색된 첫 번째 결과값이 인자로 들어온다
// replace 함수는 대체할 문자열 대신 함수 전달이 가능하다
// 함수를 전달했을 경우 return값 대로 치환됨
var result = content.replace(urlPattern, function(url){
    return '<a href="'+url+'">'+url+'</a>';
});
```
