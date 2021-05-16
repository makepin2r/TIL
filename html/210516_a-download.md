# a 태그 속성: download
- a 태그의 속성으로, 링크로 이동하는 대신 url을 저장하게 함.
- 동일 출처 url, blob:, data: 스킴에서만 작동한다.
    - 동일 출처 url은 프로토콜(ex. https://), 호스트, 포트번호가 모두 같아야 한다는 뜻이다.
```html
<a href=""data:image/png;base64,iVBORw0KGgoAAAANSUhEUg" download></a>
```
- download 속성에 값을 주면 저장시 데이터의 파일명이 된다.
```html
<!-- myFile.png 로 다운로드 된다. -->
<a href=""data:image/png;base64,iVBORw0KGgoAAAANSUhEUg" download="myFile"></a>
```
---
### 참고
- [MDN a 태그](https://developer.mozilla.org/ko/docs/Web/HTML/Element/a)