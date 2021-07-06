# Deep Selector (::v-deep)
## 개념
`::v-deep`이 붙은 요소는 동적으로 렌더링될 때에 vue에 로드되는 타이밍을 체크한다.  
만약 어떤 컴포넌트에서 사용되는 자식 컴포넌트가 있을 경우 v-deep을 붙이지 않으면 이후 동적으로 생성되어야 할 때를 체크하지 못하고 css가 무시된다.

vue2.0 이전 버전까지는 `>>>`이 사용되었지만 vue3.0부터는 `::v-deep`이 사용된다.


## 참고 사이트
- https://www.telerik.com/blogs/understanding-vue-deep-css-selector