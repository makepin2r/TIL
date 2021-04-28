# 생성자와 new
- 객체지향 프로그래밍의 기본 형태 : 연관된 변수와 메소드를 **객체**로 그룹핑해서 만든 독립적인 부품을 조립하는 방식.

javascript는 일반 객체지향 언어가 아닌 prototype-based programming 언어라고 표현한다. 따라서 객체를 다루는 메커니즘이 다소 독특하다.

## 객체 생성하기
### 기본적인 방법
- 객체 리터럴
```javascript
var person = {} // 객체 리터럴. Object가 생성된다.
person.name = 'egoing'; // 프로퍼티(=변수, 속성) 인 name을 생성
person.introduce = function(){
    return 'My name is ' + this.name; //this는 이 함수를 담고 있는 주체인 person이 된다.
} // 메소드인 introduce 생성

document.write(person.introduce());
```
위의 코드에서 객체의 정의 부분을 응집하면
```javascript
var person = {
    'name' : 'egoing',
    'introduce' : function(){
        return 'My name is '+this.name;
    }
}
document.write(person.introduce());
```
---
## 생성자
- 객체를 생성하는 역할을 하는 함수
    - 같은 구조의 객체를 여러 개 생성해야 할 때(재활용), 하나의 객체를 만들어놓고 생성자를 통해 반복 생성할 수 있음.
### new 키워드
- `new` 키워드를 이용해 생성자 함수를 만든다.
- new 키워드가 함수 앞에 붙으면 일반 함수가 아닌 **객체의 생성자**가 된다. 
    - return값을 뱉어주는 일반 함수와 달리,  
    - `new [함수]();` 는 새로운 객체를 만든 뒤 리턴해준다.
```javascript
function Person (){} // 함수

var p1 = Person(); // 일반 함수 호출해 대입
console.log(p1); // return이 정의되지 않은 함수이므로, undefined가 들어있다.

var p2 = new Person(); // 함수 호출이 아닌 person 이라는 객체의 생성자
console.log(p2) // Person {}, 즉 비어있는 person 객체가 담긴다
```

### 초기화
- 파라미터를 활용해 넣어줄 속성의 값을 전달하여 객체를 생성할 수 있다. (= **초기화**) -> 코드의 재사용성이 높아진다
    - 생성자 함수는 보통 대문자로 시작 (일반 함수와 구분하기 위해)
```javascript
    function Person(name){ 
        this.name = name;
        this.introduce = function(){
            return 'My name is '+this.name; 
        }   
    }
    var p1 = new Person('egoing'); 
    document.write(p1.introduce()+"<br />");
    
    var p2 = new Person('leezche');
    document.write(p2.introduce());
```