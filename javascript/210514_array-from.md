# Array.from()
객체를 복사해 새로운 Array 객체(배열)를 만드는 함수 
- 배열로 변환될 수 있는 유사 배열 객체(인덱싱 요소와 length가 있는 객체)나 iterable한 객체(Map, Set 등)를 매개변수로 받는다.
- 해당 객체를 얕은 복사하여 배열 인스턴스를 반환한다.

```javascript   
//// nomad coder에서 얻은 예시

// jsColor라는 클래스명을 가진 모든 요소들을 가져온다. 객체 상태
const colors = document.getElementsByClassName("jsColor"); 

// colors 객체를 배열화한 뒤 각 요소를 돌며 이벤트리스너를 추가한다.
Array.from(colors).forEach(color => color.addEventListener("click", handleColorClick));
```