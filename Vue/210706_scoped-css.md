# Scoped CSS
Vue 컴포넌트에서 사용되는 `style` 태그에 scoped를 사용하면 해당 컴포넌트에만 적용된다.  
그 이유는 Vue 컴포넌트가 생성될 때 해당 태그에 고유한 해시값이 붙는데, scoped를 사용하면 컴포넌트에 연결된 css 내 선택자에 모두 해시값을 동일하게 붙여주기 때문이다.

```html
<!-- 원래 코드 -->
<style scoped>
    div {
        background: #fff;
    }
</style>

<!-- 렌더링 시 -->
<style scoped>
    /* 아래와 같이 해시값이 붙은 상태로 변형된다. */
    div[data-v-12345] {
        background: #fff;
    }
</style>
```
