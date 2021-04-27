# 클로저
## 내부함수와 외부함수
- 함수 안에 함수를 선언하는 경우
  - 감싸고 있는 함수: 외부함수
  - 안에 있는 함수 : 내부함수
- 내부함수는 외부함수의 지역변수에 접근할 수 있다.
```javascript
function outter(){ // 외부함수
    var title = 'coding everybody'; 
    function inner(){ // 내부함수, 일종의 지역변수처럼
        alert(title); //'coding everybody'
    }
    inner();
}
outter();
```
---
## 클로저의 의미
- 외부함수는 외부함수의 지역변수를 사용하는 내부함수가 소멸할 때까지 함께 소멸하지 않고 유지된다.
- 내부함수는 외부함수의 지역변수에 접근할 수 있다는 특성을 이용.
    - 렉시컬 스코프의 특성에 의해 내부함수에서 외부함수의 지역변수에 접근할 수 있다.
    - 외부함수가 이미 실행되어 종료했더라도, 내부함수가 여전히 소멸하지 않았다면 내부함수가 접근하는 외부함수의 변수는 원래의 렉시컬 스코프인 외부함수를 기억하며 접근 가능하게 유지된다.
---
## 클로저 응용 : private variable
- 변수를 아무나 변경할 수 없도록 숨기는 방법 
  - 변수를 감싸는 객체 외부에서는 변수에 접근할 수 없도록 하는 것이 private 속성이다. 
  - 예기치 못한 값 변경을 방지할 수 있다.

```javascript
// factory_movie라는 외부 함수에
// 리턴값 객체 속 두 메소드가 내부 함수인 형태
function factory_movie(title){
    return {
        get_title : function (){
            return title;
        },
        set_title : function(_title){
            if(typeof _title === 'String') {
              // 유효하지 않은 타입을 방지할 수 있다
              title = _title;
            } else {
              alert('제목은 문자열이어야 합니다.');
            }
        }
    }
}
ghost = factory_movie('Ghost in the shell');
matrix = factory_movie('Matrix');
 
alert(ghost.get_title());
alert(matrix.get_title());
 
ghost.set_title('공각기동대');
 
alert(ghost.get_title());
alert(matrix.get_title());
```
- ghost와 matrix에 저장된 `factory_movie()`의 결과는 각각 별개의 클로저이다. 서로 완전히 독립되어 각각의 객체에 들어간 title 인자를 갖고 있다. 
- 동일 외부함수 안에서 만들어진 내부함수나 메소드는 외부함수의 지역변수를 공유한다. 따라서 `set_title()`을 이용해 값을 바꾸면 `get_title()`에 변경된 값이 출력된다.

---
## 클로저 대표 예제

```javascript
var arr = []
for(var i = 0; i < 5; i++){
    arr[i] = function(){
        return i; // 전역변수 i를 가리키기 때문에
    }
}
for(var index in arr) {
    console.log(arr[index]()); // 5가 5번 출력된다.
}
```
위의 예제에서 0~4가 출력되게끔 수정하려면 클로저를 활용한다.
```javascript
var arr = []
for(var i = 0; i < 5; i++){
    arr[i] = function(id){
      return function(){
          return id;
      }
    }(i);
}
for(var index in arr) {
    console.log(arr[index]()); // 0~4가 출력된다.
}
```

---
#### 참고한 곳
- https://leehwarang.github.io/2019/10/07/scope.html