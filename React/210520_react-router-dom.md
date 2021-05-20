# React Router DOM : 리액트에서의 라우팅
## 패키지 사용 방법
### 설치
```
npm install react-router-dom
```
### 기본 사용법
1. import
```javascript
import { HashRouter, Route } from "react-router-dom";
```
2. 최상단? 컴포넌트에 `Route` 컴포넌트로 경로를 설정하고, Router 컴포넌트로 감싼다.
```javascript
import { HashRouter, Route } from "react-router-dom";
import About from "./routes/About"; // 연결할 스크린

function App(){
  return (
    <HashRouter>
      <Route path="/about" exact={true} component={About} />
    </HashRouter>
  );
}
```

## `<Route />` 컴포넌트
### Route 컴포넌트의 주요 props
- component: 렌더링할 스크린 컴포넌트
- path: 라우팅 경로
- **exact** 
    - Router는 매치되는 모든 url의 Route를 렌더한다. 겹치는 부분이 있을 경우 모두 렌더해버린다. (ex: `/home` 과 `/home/introduction` 이 있을 경우 : 둘다 렌더함)
    - 불리언 값으로 exact에 `true`를 주면 path 속성값과 정확히 일치하는 경우에만 렌더링됨
### Route props
https://reactrouter.com/web/api/Route/route-props 참고
- match
- location
- history
### 동적 라우팅
`:변수명` 의 형태로 path에 추가하면 변수처럼 인식하며, 동적으로 들어오는 값에 따라 경로를 만들 수 있다.
```javascript
<Route path="/movie/:id" component={Detail} />
```
```javascript
function Movie( { id, year, title, summary, poster, genres } ) {
    return (
        <Link to={{
            pathname: `/movie/${id}`, // id에 따라 경로가 동적으로 구성된다
            state: {
                year,
                title,
                summary,
                poster,
                genres
            }
        }}></Link>
    );
};
```

## `<Link />` 컴포넌트
- Router 안에서는 `a` 태그 대신 Link 컴포넌트를 사용한다
    - `a`와 href 속성을 사용할 경우 페이지가 새로고침되므로.
```javascript
import { Link } from "react-router-dom";

<Link to="/">Home</Link>
```
- 주의! Link 컴포넌트는 Router 안에서만 동작한다.
### Link 컴포넌트의 주요 props
- **to** : String으로 경로를 받을 수도 있고, 함수나 object를 받을 수도 있다.
    - https://reactrouter.com/web/api/Link/to-object 참고

    - object로 여러가지 값을 받아 데이터를 보내줄 수 있다 [위의 두 번째 코드 스니펫 참고](###-동적-라우팅)
