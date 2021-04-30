# 상속 Inheritance
## 상속이란?
- 어떤 객체의 로직을 다른 객체가 그대로 물려받을 수 있는 기능
- 물려받을 뿐만 아니라 기존 로직을 수정하여 맥락에 맞는 새로운 객체를 생성할 수 있다
  
```javascript
    function Person(name){
        this.name = name;
        this.introduce = function(){
            return 'My name is '+this.name; 
        }   
    }
    var p1 = new Person('egoing');
    document.write(p1.introduce()+"<br />");
```
위의 코드를 아래와 같이 변경
- 객체의 `prototype`이라는 프로퍼티 객체를 이용해 속성과 메소드들을 정의할 수 있다.
```javascript
    function Person(name){
        this.name = name;
    }
    // prototype 객체를 이용한 값 할당
    Person.prototype.name=null;
    Person.prototype.introduce = function(){
        return 'My name is '+this.name; 
    }
    var p1 = new Person('egoing');
    document.write(p1.introduce()+"<br />");
```

## 상속의 사용법
- 상속할 생성자를 호출하면 자바스크립트는 prototype 속성을 생성자 함수가 가지고 있는지 확인한다.
- 그리고 그 prototype 속성들을 가진 똑같은 객체를 만들어서 리턴해준다.
- 상속받을 함수의 prototype 객체에 리턴된 객체를 넣어주면 상속 관계가 된다.

```javascript
    // Person을 상속하는 Programmer
    function Programmer(name) {
        this.name = name;
    }
    Programmer.prototype = new Person(); // 상속하기

    var p1 = new Programmer('hirobot');
    document.write(p1.introduce() + "<br />");
```

## 기능의 추가
- 상속받은 객체의 prototype에 새로운 기능을 추가해주면 된다.
```javascript
// Person을 상속받은 Programmer 객체에...
Programmer.prototype.coding = function(){
    return "Hello world";
} // coding 이라는 메소드 추가

var p1 = new Programmer('hirobot');
document.write(p1.coding() + "<br />"); // "Hello world"
```

