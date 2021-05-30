# 브라우저 접두어 Vendor Prefix

CSS 표준으로 채택되기 전 과도기적인 기능들의 이슈 점검을 위해 브라우저별로 대응하기 위한 방식.

CSS 속성명 앞에 브라우저별 지정된 접두어를 붙여 사용한다. 웹킷 기반 브라우저의 접두어는 -webkit-이며, 현재 Chrome, Safari 등의 브라우저에는 해당 접두어를 사용한다. 

접두어가 붙은 속성들을 모두 작성 후 마지막에 표준 속성을 적는 것이 일반적이다. 각각의 브라우저는 자신이 이해할 수 있는 접두어를 찾을 때까지 타 접두어 속성은 무시하며,  표준을 지원하는 경우 맨 마지막의 표준 속성을 실행한다.

```css
div {
  -moz-border-radius: 10px;
  -webkit-border-radius: 10px; /* Webkit 기반의 브라우저 - Chrome, Safari */
  -o-border-radius: 10px;
  border-radius: 10px; /* 표준 */
}
```

